pipeline {
agent any
stages{
stage('Package') {
steps {
checkout scmGit(branches: [[name: '*/master']], extensions: [],
userRemoteConfigs: [[url: 'https://github.com/traccytian/Teedy_2024.git']])
sh 'mvn -B -DskipTests clean package'
}
}
// Building Docker images
stage('Building image') {
steps{
//your command
}
}
// Uploading Docker images into Docker Hub
stage('Upload image') {
steps{
//your command
}
}
//Running Docker container
stage('Run containers'){
steps{
script{
//your command
}
}
}
}
}
