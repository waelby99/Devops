pipeline {
    agent any

stages {
        stage('Checkout Git') {
            steps {
                echo 'Pulling from git ';
                git branch: 'Wael', credentialsId: '486a5359-e642-41df-bbc8-d1cfd0e3ad20', url: 'https://github.com/yasminenasfi2001/DevOps_Station_Ski.git'
            }
        }
    stage('Compiling :clean and compile') {
                    steps {
                    echo 'Compiling ... ';
                        sh 'mvn clean'
                        sh 'mvn compile'
                    }
                }
    stage('Run Unit Tests') {
                   steps {
                   echo 'Testing course service methods  ... ';
                        sh 'mvn test -X'
                        sh'mvn jacoco:report'
                   }
               }
       stage('Static Code Analysis with SonarQube') {
           steps {
               withSonarQubeEnv('sonarqube') {
                   sh 'mvn sonar:sonar -Dsonar.coverage.jacoco.xmlReportPaths=**/target/site/jacoco/jacoco.xml'
               }
           }
       }
        stage('Nexus deploment') {
                   steps {
                   echo 'starting deployment on nexus'
                     sh 'mvn package'
                     sh 'mvn deploy' }
       }
       stage('Spin up Docker containers') {
                   steps {
                       script {
                           sh 'docker compose -f docker-compose.yml up -d'
                       }
                   }
       }
       stage('Build and Push Docker Images') {
           steps {
               script {
                   withCredentials([usernamePassword(credentialsId: '901bd5e9-89d7-4f31-b1d1-5536bd3ac582', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_TOKEN')]) {
                       sh "echo $DOCKER_TOKEN | docker login -u $DOCKER_USERNAME --password-stdin"
                       sh "docker tag stationski-wael-app:latest ${waoul/gestionstationski}:latest"
                       sh "docker push ${waoul/gestionstationski}:latest"
                       sh "docker tag mysql:8.0 ${waoul/gestionstationskidb}:latest"
                       sh "docker push ${waoul/gestionstationskidb}:latest"
                   }
               }
           }
       }

}
}