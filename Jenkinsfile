@Library('Jenkins-shared-library') _

def configMap = [
    project: "roboshop",
    component: "catalogue"
]

echo "Triggering the shared library pipeline"

if (env.BRANCH_NAME.equalsIgnoreCase('main')) {
    echo "Main branch"
} else {
    testpipeline(configMap)
}