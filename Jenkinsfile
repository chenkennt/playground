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

node {
    stage('Example') {
        sh 'echo Example'
        // azureDownload storageCredentialId: 'kenchenjenkinsdemotmpl', downloadType: [value: 'container', containerName: 'demo'], includeFilesPattern: '**', downloadDirLoc: 'temp'
        // azureUpload storageCredentialId: 'kenchenjenkinsdemotmpl', filesPath: 'temp/**', containerName: 'demo2', virtualPath: env.BUILD_TAG
        // default variable name
        withCredentials([azureCredentials('vs_china_jenkins')]) {
            echo "default variable name"
            echo "${AZURE_SUBSCRIPTION_ID}"
            echo "${AZURE_CLIENT_ID}"
            echo "${AZURE_CLIENT_SECRET}"
            echo "${AZURE_TENANT_ID}"
            sh 'az logout || true'
            sh 'az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID'
            sh 'az account show'
        }
        // custom name
        withCredentials([azureCredentials(
            credentialsId: 'vs_china_jenkins', subscriptionIdVariable: 'SUBS_ID', clientIdVariable: 'CLIENT_ID', clientSecretVariable: 'CLIENT_SECRET', tenantIdVariable: 'TENANT_ID')]) {
            echo "custom name"
            echo "${SUBS_ID}"
            echo "${CLIENT_ID}"
            echo "${CLIENT_SECRET}"
            echo "${TENANT_ID}"
        }
    }
}
