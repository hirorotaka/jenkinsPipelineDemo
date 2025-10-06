pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from  Github hook triger World'
            }
        }    
        stage('Build') {
            steps {
                echo 'Building'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp FilePath(/var/lib/jenkins/workspace/JenkinsPipeline/index.html) s3://test-env-jenkins-takada-20251-07')
                }
            }
        }            
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Release') {
            steps {
                echo 'Releaseing'
            }
        }        
    }
}
