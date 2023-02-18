pipeline {
    agent any

    stages {
        stage('Fetch issue and label information') {
            steps {
                script {
                    def issueNumber = env.CHANGE_ID
                    def labelName = env.CHANGE_TARGET
                    echo "Issue number: ${issueNumber}"
                    echo "Label name: ${labelName}"
                }
            }
        }
        stage('Run build steps') {
            steps {
                // Insert build steps here
            }
        }
    }

    // Define the conditions for the pipeline to run
    options {
        skipDefaultCheckout true
    }
    environment {
        CHANGE_ID = "${env.CHANGE_ID}"
        CHANGE_TARGET = "${env.CHANGE_TARGET}"
    }
    when {
        expression { env.CHANGE_ID && env.CHANGE_TARGET }
    }
}

