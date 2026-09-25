node ('agent3-docker'){
    stage('Get code'){
        checkout scm
    }
    stage('build java app'){
        sh 'mvn clean package'
    }
    stage('build image') {
    sh 'docker build -t motamerf/java-app:latest .'
    }
    stage('login to docker hub') {
        withCredentials([usernamePassword(credentialsId: 'Docker Creds', 
                                          usernameVariable: 'DOCKER_USER', 
                                          passwordVariable: 'DOCKER_PASS')]) {
            
            // Masked variables are accessible inside this block
            sh 'docker login -u "$DOCKER_USER" -p "$DOCKER_PASS"'
        }
    }
    stage('deploy image '){
        sh 'docker push java-app:latest'
    }
    stage('deploy'){
        sh 'docker rm -f java-running || true'
        sh 'docker run -d -p 8090:8090 --name java-running java-app:latest'
    }
}
