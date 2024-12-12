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
    }
}
