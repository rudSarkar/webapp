pipeline {
    // specifie machine to execute the pipeline
    agent any
    // tool to execute few steps
    tools {
        maven 'Maven'
    }
    // multiple stages can be defined
    stages {
        stage('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Check Git Secrets') {
            steps {
                sh 'docker run -v /var/run/docker.sock:/var/run/docker.sock -ti docker'
                sh 'docker pull gesellix/trufflehog'
                sh 'docker run -t gesellix/trufflehog --json https://github.com/rudSarkar/webapp/ > trufflehog'
            }
        }
    }
}
