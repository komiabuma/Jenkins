pipeline {
    agent { label 'test' }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'test', url: 'https://github.com/yourusername/yourrepo.git'
            }
        }

        stage('Deploy to Test Server') {
            steps {
                sh '''
                echo "Deploying to Test Server..."
                rsync -avz --delete ./ user@test_server_ip:/var/www/test_app/
                '''
            }
        }
    }
}
