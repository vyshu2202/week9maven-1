pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'
    }
    stages {
        stage('Checkout & Clean') {
            steps {
                cleanWs()
                git url: 'https://github.com/vyshu2202/week9maven-1.git'
            }
        }
        stage('Build') {
            steps {
                // Run mvn commands from root, no subdirectory change
                bat "mvn clean install"
            }
        }
        stage('Test') {
            steps {
                bat "mvn test"
            }
        }
        stage('Package') {
            steps {
                bat "mvn package"
            }
        }
    }
    post {
        success {
            echo 'Build completed successfully!'
            archiveArtifacts 'target/*.jar'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
------------------web -----------------------
    pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/lohithak28/week9maven-1.git'
            }
        }

        stage('Build WAR') {
            steps {
                bat "mvn clean package"
            }
        }

        stage('Archive WAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat '''
                    copy target\\*.war C:\\tomcat9\\webapps\\ /Y
                    net stop "Tomcat9"
                    net start "Tomcat9"
                '''
            }
        }
    }
}
