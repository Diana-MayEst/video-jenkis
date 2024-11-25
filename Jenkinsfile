pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = 'mi-proyecto'
    }

    stages {
        stage('Pull Docker Images') {
            steps {
                script {
                    // Descargar las últimas imágenes de Docker (si es necesario)
                    sh 'docker-compose pull'
                }
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    // Levantar los contenedores en modo background (-d) y construir las imágenes si es necesario
                    sh 'docker-compose up -d --build'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    // Limpiar contenedores no utilizados si es necesario
                    sh 'docker system prune -f'
                }
            }
        }
    }
}
