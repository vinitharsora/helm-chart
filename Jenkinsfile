pipeline {
    agent any
  
    tools {nodejs "nodejs"}
    stages {
        stage('Build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'a5']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'cloudcreds', url: 'https://github.com/Shrawani04/helm-chart.git']]])
                sh "ls -lart ./*"
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
		         npm install --save-dev semantic-release
		         npx semantic-release
		        '''
		    }
		}
    }
}