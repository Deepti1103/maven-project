Pipeline{
any agent{
Stages{
Stage('SCM Checkout') {
git 'https://github.com/Deepti1103/maven-project.git'}

Stage('compile source code'){
Steps{
withMaven (maven: 'My_maven'){
sh 'mvn compile'
}}
Stage('Test source code'){
Steps{
withMaven (maven: 'My_maven'){
sh 'mvn test'
}}
Stage('Package source code'){
Steps{
withMaven (maven: 'My-maven'){
sh 'mvn package'
}}
Stage('Install source code'){
Steps{
withMaven (maven: 'My_maven'){
sh 'mvn install'
}}
}
}
}
}
