pipeline {
    agent any
    parameters {
        string(name: 'BASE_BUILD', description: 'Build number to deploy')
    }
    stages {
        stage('Deploy') {
            steps {
                script {
                    def isWindows = (env.BUILD_OS == 'Windows_NT')
                    
                    if (isWindows) {
                        bat 'echo Using build number %BASE_BUILD%'
                        bat 'call deploy.bat --build %BASE_BUILD%'
                    } else {
                        sh "echo Using build number $BASE_BUILD"
                        sh "./deploy.sh --build $BASE_BUILD"
                    }
                }
            }
        }
    }
    post {
        success {
            echo 'Build and deployment succeeded!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}
