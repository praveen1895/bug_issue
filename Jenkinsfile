pipeline {
    agent any

    environment {
        // Replace "my-label" with the name of the label you want to trigger the pipeline on
        MY_LABEL = "my-label"
    }

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
            when {
                allOf {
                    expression { env.CHANGE_ID && env.CHANGE_TARGET }
                    expression { env.CHANGE_TARGET.toLowerCase() == env.MY_LABEL.toLowerCase() }
                }
            }
        }
        stage('Run build steps') {
            steps {
                // Insert build steps here
            }
        }
    }
}

