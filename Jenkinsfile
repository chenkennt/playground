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

def shWithOutput(def script) {
    sh (script: script, return Stdout: true)
}

node {
    withCredentials([azureServicePrincipal('vs_china_jenkins')]) {
        sh '''
            az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID
            az account set -s $AZURE_SUBSCRIPTION_ID
        '''
    }
    sh 'az account show'
    def pubSettings = shWithOutput 'az webapp deployment list-publishing-profiles -g kenchenwebapp1 -nkenchenwebapp1'
    echo pubSettings
    sh 'az account show'
    sh 'az logout'
}
