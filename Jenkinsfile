pipeline {
environment {
registry = "drsureshbrathod/myrepo"
registryCredential = '363c3585-5530-4e49-8f8d-7b012c604bef'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git  'https://github.com/drsureshbrathod/web_login_automation.git'}
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
docker.withRegistry( '', drsureshbrathod ) {
dockerImage.push()
}
}
}
}
stage('Cleaning up') {
steps{
sh "docker rmi $registry:$BUILD_NUMBER"
}
}
}
}
