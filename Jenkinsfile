pipeline {
    agent any
    environment {
        GIT_REPO = 'https://github.com/praveen1895/jen.git'
        GIT_CREDENTIALS_ID = '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'
        LABEL_NAME = 'bug1'
        LABEL_COLOR = 'ff0000'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: GIT_CREDENTIALS_ID, url: GIT_REPO]]])
            }
        }
        stage('Build') {
            when {
                expression {
                    env.CHANGESet_LABEL_NAME
                }
            }
            steps {
                sh '''
                    #!/bin/bash
                    echo "Build started"
                    # Build your code here
                    # ...
                    echo "Build finished"
                '''
            }
        }
    }
    post {
        always {
            script {
                if (env.CHANGESet_LABEL_NAME) {
                    def webhook_url = "http://ec2-15-206-146-13.ap-south-1.compute.amazonaws.com:8080/github-webhook/"
                    def payload = [
                        label: env.CHANGESet_LABEL_NAME,
                        event: "created"
                    ]
                    def headers = [
                        "Content-Type": "application/json"
                    ]
                    def response = httpRequest url: webhook_url, contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody: JsonOutput.toJson(payload), customHeaders: headers
                    echo "Webhook triggered with response code: ${response.status}"
                }
            }
        }
    }
}

