pipeline {

    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {

        stage('GIT') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Salsabil-23/StudentManagement.git'
            }
        }

        stage('Compile Stage') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Unit Testing Stage') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package Stage') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy Stage') {
            steps {
                sh 'mvn deploy'
            }
        }

    }

    post {
        always {
            echo "=== Pipeline terminé ==="
        }
        success {
            echo "=== Pipeline exécuté avec succès ==="
        }
        failure {
            echo "=== Le pipeline a échoué ==="
        }
    }
}
