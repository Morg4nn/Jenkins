pipeline {
    agent any
    stages {
        stage('Install Apache') {
            steps {
                script {
                    // Оновлення системи та встановлення Apache2
                    sh '''
                    sudo apt update -y
                    sudo apt install apache2 -y
                    sudo systemctl start apache2
                    sudo systemctl enable apache2
                    '''
                }
            }
        }

        stage('Verify Installation') {
            steps {
                script {
                    // Перевірка, чи працює Apache
                    sh 'sudo systemctl status apache2'
                }
            }
        }

        stage('Check Apache Logs for Errors') {
            steps {
                script {
                    // Перевірка наявності помилок 4xx і 5xx в логах Apache
                    sh '''
                    sudo tail -n 100 /var/log/apache2/error.log | grep -E '4[0-9]{2}|5[0-9]{2}'
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs for errors.'
        }
    }
}
