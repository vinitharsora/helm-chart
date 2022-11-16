

pipeline {
    agent any
    
    tools {nodejs "node"}
    
    environment {
        GITHUB_TOKEN = credentials('admin')
    }

    stages {
        stage('Checkout code') {
            steps {
                cleanWs()
                checkout scm
            }
        }
        stage('Create Semantic Versioning') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'admin', usernameVariable : 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                    npm install @semantic-release/git
                    npm install @semantic-release/github
                    npm install @semantic-release/changelog
                    npm install semantic-release-helm
                    ls -al
                    GITHUB_TOKEN=$PASSWORD npx semantic-release
                    '''
                }
            }
        }
    }
    post { 
        always {
            echo 'Post task!'
        }
    }
}