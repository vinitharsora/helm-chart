pipeline {
    agent any
    environment{
        GITHUB_TOKEN = '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'
    }
    tools {nodejs "nodejs"}
    stages {
        stage('Build') {
            steps {
                cleanWs()
                // sh'npm cache clean'
                checkout([$class: 'GitSCM', branches: [[name: 'a5']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'cloudcreds', url: 'https://github.com/Shrawani04/helm-chart.git']]])
                sh "ls -lart ./*"
                sh 'cat package.json'

            }
        }
		stage('semantic-release')
		{
		    steps{
		        sh '''
                pwd
		        npm install @semantic-release/exec -D
                pwd
                ls -lrta
                cat package.json
                npx semantic-release
                npx semantic-release-cli
		        '''
		    }
		}
    }
    // post{
    //     always{
    //         cleanWs()
    //     }
    // }
}