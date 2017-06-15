//pipeline {
//    agent any
//    stages {
//        stage('Example') {
//            steps {
//                sh 'echo Example'
//                azureDownload storageCredentialId: 'kenchenjenkinsdemotmpl', downloadType: [value: 'container', containerName: 'demo'], includeFilesPattern: '**', downloadDirLoc: 'temp'
//                azureUpload storageCredentialId: 'kenchenjenkinsdemotmpl', filesPath: 'temp/**', containerName: 'demo2', virtualPath: env.BUILD_TAG
//            }
//        }
//    }
//}

import groovy.json.JsonSlurper

node {
    withCredentials([azureServicePrincipal('vs_china_jenkins')]) {
        sh '''
            az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID
            az account set -s $AZURE_SUBSCRIPTION_ID
        '''
    }
    sh 'az account show'
    def pubProfilesJson = sh script: 'az webapp deployment list-publishing-profiles -g kenchenwebapp1 -n kenchenwebapp1', returnStdout: true
    def pubProfiles = new JsonSlurper().parse(pubProfilesJson)
    echo pubProfiles
    sh 'az account show'
    sh 'az logout'
}
