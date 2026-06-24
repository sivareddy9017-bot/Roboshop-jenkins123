pipeline {
    agent {
        node {
            label 'Java' 
        } 
    }
    environment {
        appVersion = ""
    }
    options {
        // disableConcurrentBuilds()
        timeout(time: 5, unit: 'MINUTES')
    }
   /* parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    } */
      stage('Read Version') {
       steps {
           script {
            def packageJson = readJSON file: 'package.json'
            appVersion = packageJson.version
            echo "Building version ${appVersion}"
        }
    }
}
        stage('Install Dependencies') {
            steps {
                script{
                    sh """
                        npm install
                    """
                }
            }
        }
        stage('Build Image') {
            steps {
                script{
                    sh """
                       docker build -t catalogue:${appVersion} .
                    """
                }
            }
        }
        /* stage('Test') {
            steps {
               script{
                    sh """
                        echo "Test123"
                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.TOGGLE}"
                        echo "Choice: ${params.DEPLOY}" 
                        echo "Password: ${params.PASSWORD}"
                    """
                }
            }
        } */
        /* stage('Deploy') {
            when {
                expression { "${params.DEPLOY}" == "true" }
            }

            /* input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            } 
            steps {
                script{
                    sh """
                        echo "Deploying"
                    """
                }
            }
        } */
    }
}

    // post build
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        success {
            echo "pipeline success"
        }
        failure {
            echo "pipeline failure"
        }
    }

