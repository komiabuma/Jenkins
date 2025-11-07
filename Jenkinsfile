pipeline {
    agent { label 'test' }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'test', url: 'https://github.com/komiabuma/Jenkins.git'
            }
        }

        stage('Deploy to Test Server') {
            steps {
                sh '''
                echo "Deploying to Test Server..."
                rsync -avz --delete ./ ubuntu@18.222.214.160:/var/www/test_app/
                '''
            }
        }
    }
}
