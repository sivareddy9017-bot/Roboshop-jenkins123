@Library('Jenkins-shared-library') _

def configMap = [
    project: "nandyala-siva",
    component: "ROBOSHOP-JENKINS123"
]

echo "Triggering the shared library pipeline"

if (env.BRANCH_NAME.equalsIgnoreCase('main')) {
    echo "Main branch"
} else {
    testpipeline(configMap)
}

nandyala-siva-sample-jenkinsfile