pipeline {
    agent any

    stages {
        // Clona el repositorio (si lo tienes en Git)
        stage('Checkout') {
            steps {
                checkout scm  // Si usas control de versiones
                // Si no, Jenkins usará los archivos directamente
            }
        }

        // Ejecuta el script Python
        stage('Ejecutar Python') {
            steps {
                script {
                    // Verifica si el archivo existe
                    if (fileExists('main.py')) {
                        echo '✅ Ejecutando main.py...'
                        bat 'py main.py'  // Para Windows (usa 'python3' en Linux)
                    } else {
                        error('❌ Error: main.py no encontrado.')
                    }
                }
            }
        }
    }
}