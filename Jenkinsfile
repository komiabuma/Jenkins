pipeline {
    agent { label 'test' }  // Jenkins Node label
    environment {
        TEST_SERVER = "ubuntu@18.222.214.160"
        PROD_SERVER = "ubuntu@3.12.111.192"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: env.BRANCH_NAME, url: 'https://github.com/komiabuma/Jenkins.git'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'test') {
                        echo "Deploying to Test Server..."
                        sh 'rsync -avz --delete ./ ${TEST_SERVER}:/var/www/test_app/'
                    } else if (env.BRANCH_NAME == 'prod') {
                        echo "Deploying to Prod Server..."
                        sh 'rsync -avz --delete ./ ${PROD_SERVER}:/var/www/prod_app/'
                    } else {
                        echo "Branch ${env.BRANCH_NAME} not set for deployment."
                    }
                }
            }
        }
    }
}
