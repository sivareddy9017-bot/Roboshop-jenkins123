pipeline {
    agent {
        node {
            label 'Java' 
        } 
    }
    environment {
        appVersion = ""
        Acc_id="553490164630"
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
      stages {
         stage ('Read Version') {
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
                    withAWS(credentials: 'AWS', region: 'us-east-1'){
                    sh """
                        aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ${Acc_id}.dkr.ecr.us-east-1.amazonaws.com
                        docker build -t ${Acc_id}.dkr.ecr.us-east-1.amazonaws.com/roboshop/catalogue:${appVersion} .
                        docker push ${Acc_id}.dkr.ecr.us-east-1.amazonaws.com/roboshop/catalogue:${appVersion} .
                    """
                }
            }
        }
        
}
}