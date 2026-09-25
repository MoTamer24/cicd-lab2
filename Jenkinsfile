node ('agent3-docker'){
    stage('Get code'){
        checkout scm
    }
    stage('build java app'){
        sh 'mvn clean package'
    }
    stage('build image') {
    sh 'docker build -t java-app:latest .'
    }
}