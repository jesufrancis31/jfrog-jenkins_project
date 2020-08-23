node{
 
 properties([
    buildDiscarder(logRotator(numToKeepStr: '3')),
    pipelineTriggers([
        pollSCM('* * * * *')
    ])
])

 def mavenHome = tool name: 'Maven_Latest', type: 'maven'
 
 stage('CheckoutCode') {
 git branch: 'master', credentialsId: '7ef842c1-5ab7-42f7-8009-61b075598acc', url: 'https://github.com/jesufrancis31/jfrog-jenkins_project.git'
 }  
  
  stage('Build') {
 
    sh "${mavenHome}/bin/mvn clean package install"
  } 
  
  stage('UploadArtifactIntoJFrog') {
 
 sh "${mavenHome}/bin/mvn deploy"
 }  
   stage('SendEmailNotification'){
  emailext body: '''Build is Over

  Regards,
  Jesu Francis S,
  9345812606.
  ''', subject: 'Build is Over', to: 'jesufrancis31@gmail.com'
  } 
    
    
}
