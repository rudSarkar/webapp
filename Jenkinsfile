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
    }
}
