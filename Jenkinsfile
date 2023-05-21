pipeline {
    agent any

    stages {
        stage('clone SCM stage') {
            steps {
                echo 'cloning code from GIT HUB'
				git branch: 'main', credentialsId: 'GitHubcredentials', url: 'https://github.com/448krrish/E1404.git'
            }
        }
		
		stage('build artifact stage') {
            steps {
                echo 'show the source code'
				sh 'ls'
				echo 'build using maven'
				sh 'mvn clean install'
            }
        }
		
		stage('deploy to tomcat stage') {
            steps {
                echo 'deploy to tomcat application server'
				deploy adapters: [tomcat7(credentialsId: '3b2410c4-c57f-4398-848b-36557c7e5ec3', path: '', url: 'http://34.204.49.248:8090/')], contextPath: 'facebook', war: '**/*.war'
            }
        }
		
    }
}
