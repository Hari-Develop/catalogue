@Library('jenkins_shared_library') _

def configMap = [
    application: "nodejs",
    component: "catalogue"
]

if(! env.BRANCH_NAME.equalsIgnoreCase('main')){
    pipelineDession.decidePipeline(configMap)
}
else {
    echo "This is the production request"
}