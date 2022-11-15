// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                 checkout([$class: 'GitSCM', branches: [[name: 'main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'cloudcreds', url: 'https://github.com/cyse7125-fall2022-group07/helm-chart.git']]])
//                 sh "ls -lart ./*"
//             }
//         }
// 		stage('create semantic version')
// 		{
// 			steps{
//                 sh 'date'
// 			}
// 		}
//     }
// }

pipeline {
    agent any
    
    tools {nodejs "node"}
    
    environment {
        GITHUB_TOKEN = credentials('gitrepo')
    }

    stages {
        stage('Checkout code') {
            steps {
                cleanWs()
                checkout scm
            }
        }
        // stage('Build') {
        //     steps {
        //         cleanWs()
        //         checkout([$class: 'GitSCM', branches: [[name: '*/assignment5']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitrepo', url: 'https://github.com/rolwynquadras/helm-chart.git']]])
        //         // sh "ls -lart ./*"
        //     }
        // }
        stage('Create Semantic Versioning') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'gitrepo', usernameVariable : 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                    npm install --dev
                    ls -al
                    GITHUB_TOKEN=$PASSWORD npx semantic-release
                    '''
                }
                // cd ./appdeployment
                // sh '''
                // npm install --dev
                // GITHUB_TOKEN=$GITHUB_TOKEN npx semantic-release
                // '''
                // cd ./appdeployment
                // ls -al
                // sed 's/'${CURRENT_VERSION}'/'${NEXT_VERSION}'/g' ./Chart.yaml
                // cat Chart.yaml
                // echo "current vesion = ${CURRENT_VERSION}"
                // echo "next version = ${NEXT_VERSION}"
                // CURRENT_VERSION = currentVersion()
                // NEXT_VERSION = nextVersion()
            }
        }
    }
    post { 
        always {
            echo 'Post task!'
        }
    }
}