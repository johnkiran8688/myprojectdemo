pipeline {
    agent any

    tools {
        maven 'Maven_3.9'
    }

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-17-openjdk"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://your-repo-url.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive WAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build success'
        }
        failure {
            echo '❌ Build failed'
        }
    }
}
