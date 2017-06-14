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
        // default credential
        withCredentials([azureCredentials(credentialsId: 'vs_china_jenkins')]) {
            sh 'printenv'
            echo '${AZURE_SUBSCRIPTION_ID}'
            echo '${AZURE_CLIENT_ID}'
            echo '${AZURE_CLIENT_SECRET}'
            echo '${AZURE_TENANT_ID}'
            echo '${abc}'
        }
    }
}
