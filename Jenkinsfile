pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				git 'https://github.com/nikhilsharma6311/pipeline.git'
				bat 'mvn clean install'
            }
        }
        stage('Test') {
		
            steps {
                echo 'Testing..'
				bat 'mvn sonar:sonar'
				
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
				deploy adapters: [tomcat9(credentialsId: 'b8ad9081-9541-493a-8810-473547ca7cf5', path: '', url: 'http://localhost:8081/')], contextPath: 'hellowolrdtest$BUILD_NUMBER', war: '**/*.war'
            }
        }
    }
}
	
	
	
