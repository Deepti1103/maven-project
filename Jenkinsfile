pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/Deepti1103/maven-project.git'
            }
        }
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarnew') {
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
                }
            }
        }
    }
}
