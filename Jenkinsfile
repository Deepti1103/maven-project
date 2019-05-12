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
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.17.135:/var/lib/tomcat/webapps'
      }}}
	  
stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('My SonarQube Server') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'My_maven') {
                        sh 'mvn sonar:sonar clean package'
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    // Requires SonarQube Scanner for Jenkins 2.7+
                    waitForQualityGate abortPipeline: true
}}}
}
}
