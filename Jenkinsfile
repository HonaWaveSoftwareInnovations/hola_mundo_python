pipeline {
    agent any

    environment {
        // Ruta personalizada de Python (ajustada a tu sistema)
        PYTHON_PATH = "C:\\Users\\juanv\\AppData\\Local\\Programs\\Python\\Python311"
        // Agrega Python al PATH temporalmente para este job
        PATH = "${env.PYTHON_PATH};${env.PYTHON_PATH}\\Scripts;${env.PATH}"
    }

    stages {
        stage('Preparar entorno') {
            steps {
                script {
                    // Verifica que Python esté accesible
                    def pythonVersion = bat(script: 'python --version', returnStdout: true).trim()
                    echo "✅ Versión de Python detectada: ${pythonVersion}"

                    // Lista archivos para debug
                    bat 'dir /B'
                }
            }
        }

        stage('Ejecutar aplicación') {
            steps {
                script {
                    if (fileExists('main.py')) {
                        echo '🚀 Ejecutando script Python...'
                        // Opción 1: Usando la variable de entorno PATH
                        bat 'python main.py'

                        // Opción 2: Usando ruta absoluta (alternativa)
                        // bat "\"${env.PYTHON_PATH}\\python.exe\" main.py"
                    } else {
                        error('❌ Error: main.py no encontrado en el workspace')
                    }
                }
            }
        }

        stage('Post-ejecución') {
            steps {
                echo '✅ Pipeline completado exitosamente'
                // Opcional: Limpieza o notificaciones
            }
        }
    }

    post {
        failure {
            echo '❌ Pipeline falló - Revisar logs'
            // mail to: 'team@example.com', subject: 'Pipeline fallido', body: "Error en ${env.JOB_NAME}"
        }
        success {
            echo '🎉 ¡Éxito! El script se ejecutó correctamente'
        }
    }
}