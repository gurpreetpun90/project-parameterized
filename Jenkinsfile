pipeline {
    agent any
    parameters {
        run(name: 'BASE_BUILD', projectName: 'your-cipla-devlop-phase-A', description: 'Select the build to use as base')
    }
    stages {
        stage('Trigger') {
            steps {
                script {
                    if (params.BASE_BUILD) {
                        echo "Using build number ${params.BASE_BUILD}"
                        // Add your build steps here
                        sh "./deploy.sh --build ${params.BASE_BUILD}"
                    } else {
                        echo "No build number provided, skipping build."
                    }
                }
            }
        }
    }
    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
