pipeline {
    agent any

    tools {
        maven 'Maven-3.8.6'    
        jdk 'JDK-11'           
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code...'
                checkout scm
                git branch: 'main', url: 'https://github.com/DhanushNadar/simple-java-app.git'
            }
        }

        stage('Build with Maven') {
            steps {
                echo 'Running Maven clean package...'
                sh 'mvn clean package'
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running the HelloWorld program...'
                sh 'java -cp target/classes HelloWorld'
            }
        }
    }

    post {
        success {
            echo '🎉 Build and Run Successful!'
        }
        failure {
            echo '❌ Build Failed!'
        }
    }
}
