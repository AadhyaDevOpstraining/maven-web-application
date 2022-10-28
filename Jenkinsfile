node

{
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
 
 stage('checkout')
 {
 git branch: 'dev', credentialsId: 'fe3318e5-7cce-4a2e-8f22-259a3250e29f', url: 'https://github.com/AadhyaDevOpstraining/maven-web-application.git'
 } 
 /*
 stage('build')
 {
 sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.6/bin/mvn clean package"
 } 
 stage('ExcuteSonarqubereport')
 {
 sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.6/bin/mvn sonar:sonar"
 }
 stage('uplode artifact to nexus')
 {
 sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.6/bin/mvn deploy"
 }
 */
 stage('Send email notification')
 {
 emailext body: '''build over

 Thanks,
 Mallikarjun''', subject: 'Build over', to: 'aadhyadevopstraining@gmail.com'
 }
 
}
