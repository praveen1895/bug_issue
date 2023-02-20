pipeline {
    agent any

    environment {
        // Replace "my-label" with the name of the label you want to trigger the pipeline on
        MY_LABEL = "my-label"
    }

    stages {
        stage('Fetch issue and label information') {
            steps {
                sh 'echo "Fetching issue and label information..."'
            }
        }
        stage('Run build steps') {
            steps {
                // Insert build steps here
            }
        }
    }

    when {
        allOf {
            expression { env.CHANGE_ID && env.CHANGE_TARGET }
            expression { env.CHANGE_TARGET.toLowerCase() == env.MY_LABEL.toLowerCase() }
        }
    }
}

