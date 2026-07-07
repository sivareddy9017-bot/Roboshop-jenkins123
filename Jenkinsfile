@Library('Jenkins-shared-library') _

def configMap = [
    project ="nandyala-siva"
    component: "ROBOSHOP-JENKINS123"
]

echo "Trihggring the library pipeline"
if (env.BRANCH_NAME.equalsIgnoreCase('main')){
     echo "checking later"
}
else{
    testPipeline(configMap)
}

