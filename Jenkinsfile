pipeline {

    agent any

    tools {
        maven 'M2_HOME'
    }

    options {
        timeout(time: 5, unit: 'MINUTES')
    }

    environment {
        APP_ENV = "DEV"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Salsabil-23/StudentManagement.git'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build JAR') {
            steps {
                sh 'mvn clean package -DskipTests=false'
            }
        }

        stage('Show Artifacts') {
            steps {
                sh 'ls -l target/'
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
