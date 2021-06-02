node
{
  
  def mavenHome = tool name: "maven3.8.1"
  properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
  stage('CheckoutCode')
  {
   git branch: 'development', credentialsId: 'f379a34a-e7eb-4cf5-81be-b5020d902936', url: 'https://github.com/sagarvidyachohan/maven-web-application.git'
  }
 
  stage('Build')
  {
   sh "${mavenHome}/bin/mvn clean package"
  }
  /* 
  stage('ExecuteSonarQubeReport')
  {
   sh "${mavenHome}/bin/mvn sonar:sonar"
  }
  
  stage('UploadArtifactsintoNexus')
  {
   sh "${mavenHome}/bin/mvn deploy"
  }
  
  stage('DeployAppintoTomcatserver')
  {
   sshagent(['80b9531d-e4eb-49ac-b771-877bde8c1819']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.104.39:/opt/apache-tomcat-9.0.45/webapps/"
  }
  }
  */
  
  stage('SendEmailNotification')
  {
   emailext body: '''Build Over..

   Regards 
   Chohan Technologies
   9010558871''', subject: 'Build Over..', to: 'chandrasekharvalireddi@gmail.com'
  }    
      
}
