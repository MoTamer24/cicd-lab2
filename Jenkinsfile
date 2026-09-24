node ('agent3-docker'){
    stage('Get code'){
        checkout scm
    }
    stage('Build') {
    sh 'docker build -t java-app:latest .'
    }
}