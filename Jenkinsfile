pipline {
    agent any

    environment {
        S3_BUCKET = 'vue-website-123124-963709452371-ap-northeast-2-an'
        AWS_DEFAULT_REGION = 'ap-northeast-2'
    }
    stages {
        stage ('Checkout')
        steps {
            //Github
            git credentialsId: 'github-token', url: 'https://github.com/B1ackC/aws-test.git', branch: 'main'
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy to s3') {
            steps {
                sh 'aws s3 sync ./dist s3://vue-website-123124-963709452371-ap-northeast-2-an --delete'
            }
        }
    }
    post {
        success {
            echo "배포 완료"
        }
        failure {
            echo "배포 실패"
        }
    }
}
