/* 
    This is the Pretested Integration Jenkinsfile
    It enables the pretested workflow for this repository, and will automatically be picked up by Jenkins
*/
node {
    stage("checkout") {
        //Using the Pretested integration plugin to checkout out any branch in the ready namespace
        checkout(
            [$class: 'GitSCM', 
            branches: [[name: '*/ready/**']], 
            doGenerateSubmoduleConfigurations: false, 
            extensions: [[$class: 'CleanBeforeCheckout'], 
            pretestedIntegration(gitIntegrationStrategy: squash(), 
            integrationBranch: 'master', 
            repoName: 'origin')], 
            submoduleCfg: [], 
            userRemoteConfigs: [[credentialsId: 'sofusalbertsen', //remember to change credentials and url.
            url: 'git@github.com:sofusalbertsen/pretested_jenkins.git']]])
    }
    stage("test"){
        // run maven tests here
        sh 'echo testing...'
    }
    stage("publish"){
        //This publishes the commit if the tests have run without errors
        pretestedIntegrationPublisher()
    }
}
