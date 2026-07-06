@Library('Jenkins-shared-library') _

def configMap = [
    project ="roboshop"
    component: "catalogue"
]

echo "Trihggring the library pipeline"
if (env.BRANCH_NAME.equalsIgnoreCase('main')){
     echo "checking later"
}
else{
    testPipeline(configMap)
}