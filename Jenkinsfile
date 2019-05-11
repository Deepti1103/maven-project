pipeline {
agent any 
stages {
stage ('SCM Checkout') {
  steps {
    git 'https://github.com/Deepti1103/maven-project.git'}
}
stage ('compile source code') {
steps {
withMaven (maven: 'My_maven') {
sh 'mvn compile'
}}}
stage ('Test source code') {
steps {
withMaven (maven: 'My_maven') {
sh 'mvn test'
}}}
stage ('Package source code') {
steps {
withMaven (maven: 'My_maven') {
sh 'mvn package'
}}}
stage ('Install source code') {
steps {
withMaven (maven: 'My_maven') {
sh 'mvn install'
}}}
  stage ('deploy to TOMCAT'){
    steps {
      sshagent(['34b1dcd3-4f88-4661-b231-e01a5ca278dd']) {
    sh 'ssh -o StrictHostKeyChecking=no */target/*.war ec2-user@18.191.116.149:/var/lib/tomcat/webapps*
}
}
}
