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
}}
