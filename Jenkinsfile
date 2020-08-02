pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') { <3>
            steps {
                sh 'mvn -B -DskipTests clean package' <4>
            }
        }
		stage('Test') { 
		            steps {
		                sh 'mvn test' 
		            }
		            post {
		                always {
		                    junit 'target/surefire-reports/*.xml' 
		                }
		            }
		        }
    }
}