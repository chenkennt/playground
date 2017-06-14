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
        withCredentials([azureCredentials(credentialsId: 'vs_china_jenkins')]) {
            echo "default variable name"
            echo "${AZURE_SUBSCRIPTION_ID}"
            echo "${AZURE_CLIENT_ID}"
            echo "${AZURE_CLIENT_SECRET}"
            echo "${AZURE_TENANT_ID}"
        }
        // with prefix
        withCredentials([azureCredentials(credentialsId: 'vs_china_jenkins', variablePrefix: 'MY_AZURE')]) {
            echo "with prefix"
            echo "${MY_AZURE_SUBSCRIPTION_ID}"
            echo "${MY_AZURE_CLIENT_ID}"
            echo "${MY_AZURE_CLIENT_SECRET}"
            echo "${MY_AZURE_TENANT_ID}"
        }
        // custom name
        withCredentials([azureCredentials(credentialsId: 'vs_china_jenkins', subscriptionIdVariable: 'SUBS_ID', clientIdVariable: 'CLIENT_ID', clientSecretVariable: 'CLIENT_SECRET', tenantIdVariable: 'TENANT_ID')]) {
            echo "custom name"
            echo "${SUBS_ID}"
            echo "${CLIENT_ID}"
            echo "${CLIENT_SECRET}"
            echo "${TENANT_ID}"
        }
    }
}
