pipeline {
    agent any

    stages {
        stage('Clonar repositorio') {
            steps {
                echo 'Clonando el repositorio...'
                git 'https://github.com/HonaWaveSoftwareInnovations/hola_mundo_python.git'
            }
        }

        stage('Ejecutar aplicación Python') {
            steps {
                echo 'Ejecutando el archivo main.py...'
                bat 'python main.py'
            }
        }
    }
}
