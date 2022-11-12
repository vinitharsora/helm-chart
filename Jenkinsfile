pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/assignment5']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitrepo', url: 'https://github.com/rolwynquadras/helm-chart.git']]])
                sh "ls -lart ./*"
            }
        }
		stage('create semantic version')
		{
			steps{
			}
		}
		stage('semVar')
		{
		    steps{
                sh "echo('sem var')"
			}
		}
    }
}