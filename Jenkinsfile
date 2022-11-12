pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'cloudcreds', url: 'https://github.com/cyse7125-fall2022-group07/helm-chart.git']]])
                sh "ls -lart ./*"
            }
        }
		stage('create semantic version')
		{
			steps{
                sh "echo('sem var')"
			}
		}
    }
}