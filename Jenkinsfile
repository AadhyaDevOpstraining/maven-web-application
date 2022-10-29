node
{
 
 stage('checkcode')
 {
 git branch: 'dev', credentialsId: 'fe3318e5-7cce-4a2e-8f22-259a3250e29f', url: 'https://github.com/AadhyaDevOpstraining/maven-web-application.git'
 }
 stage('build')
 {
 sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.6/bin/mvn clean package"
 }
 /*
 stage('sonarexcutionreport')
 {
 sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.6/bin/mvn sonar:sonar"
 } 
 */
 stage('uplode artifact to nexus')
 {
 sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.6/bin/mvn deploy"
 }
   stage('Deploy appilcation to tomcat')
 {
 sshagent(['b9a19084-c68b-418a-85d1-3716a76be716']) {
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.21.207.25:/opt/apache-tomcat-9.0.68/webapps/"
 }
 }
  stage('Send email notification')
 {
 emailext body: '''Build over

Thanks,
Mallikarju,''', subject: 'Build over', to: 'aadhyadevopstraining@gmail.com'
 }
  stage('build auto trigger')
 {
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '4')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
 }

}
