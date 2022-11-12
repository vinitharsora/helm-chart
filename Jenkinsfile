pipeline {
    agent any
    environment{
        GITHUB_TOKEN = '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'
    }
    tools {nodejs "nodejs"}
    stages {
        stage('Build') {
            steps {

                checkout([$class: 'GitSCM', branches: [[name: 'a5']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'cloudcreds', url: 'https://github.com/Shrawani04/helm-chart.git']]])
                sh "ls -lart ./*"
                sh 'cat package.json'
                sh 'echo  { "release": { "branches": [ "a5" ] }} >> package.json'
                sh 'cat package.json'

            }
        }
		stage('install npm')
		{
			steps{
                sh """
                pwd
                date
                node --version
                npm -v
                """
                
			}
		}
		stage('semantic-release')
		{
		    steps{
		        sh '''
                pwd
		         npm install --save-dev semantic-release
		         npx semantic-release
                pwd
		        '''
		    }
		}
    }
}