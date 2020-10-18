pipeline {
environment {
registry = "ishita31/Mid1"
registryCredential = 'ishita31'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git 'https://github.com/ishitasinghal/Practice.git'
}
}
stage('Build') {
steps {
bat 'docker build -t sample-web-app .'
}
}
stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}
}
}
