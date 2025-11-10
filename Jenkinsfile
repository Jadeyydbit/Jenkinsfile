pipeline {
    agent any
    tools {
        jdk 'JDK11'        // Name of JDK configured in Jenkins (Global Tool Configuration)
        maven 'Maven3.8'   // Name of Maven configured in Jenkins (Global Tool Configuration)
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                git url: 'https://github.com/Jadeyydbit/Jenkins.git', branch: 'main'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling the project...'
                sh 'mvn compile'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project (package)...'
                sh 'mvn package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()   // Removes all files from workspace
        }
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
