@Library('Jenkins-shared-library') _

def configMap = [
    project : "nandyla-siva",
    component: "ROBOSHOP-JENKINS123"
]

echo "Trihggring the library pipeline"
if ("main".equalsIgnoreCase(env.BRANCH_NAME ?: "")) {
    echo "checking later"
} else {
    testpipeline(configMap)
}

