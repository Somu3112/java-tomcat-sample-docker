pipeline {
    agent any
	environment {
    		PATH = "/Users/nileshkumarshegokar/.jenkins/tools/hudson.tasks.Maven_MavenInstallation/auto/bin:/usr/local/bin:$PATH"
  	}
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage('Create Tomcat Docker Image'){
            steps {
                sh "pwd"
                sh "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
            }
        }

    }
}