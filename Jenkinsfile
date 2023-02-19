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

    environment {
        // Replace "my-label" with the name of the label you want to trigger the pipeline on
        MY_LABEL = "my-label"
    }

    when {
        allOf {
            expression { env.CHANGE_ID && env.CHANGE_TARGET }
            expression { env.CHANGE_TARGET.toLowerCase() == env.MY_LABEL.toLowerCase() }
        }
    }
}

