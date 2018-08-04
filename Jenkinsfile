pipeline {
    agent any

    stages {
        stage ('Check') {
            steps {
                parallel (
                    unit: {
                        sh "echo 'Unit Tests...'"
                    },
                    env: {
                        sh "env | sort -k1"
                        sh "whoami"
                    }
                )
            }
        }
        stage('Except Master') {
            when {
                not {
                    branch 'master'
               }
            }
            steps {
                sh 'echo "Except On Master Branch"'
            }
        }
        stage('Only Master') {
            when {
                branch 'master'
            }
            steps {
                sh 'echo "Only On Master Branch"'
            }
        }
        stage ('Deploy') {
            steps {
                sh "echo 'Deploying...'"
            }
        }
    }

    post {
        success {
            sh "echo 'SUCCESS'"
        }
        failure {
            sh "echo 'FAILURE"
        }
    }
}
