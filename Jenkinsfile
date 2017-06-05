pipeline {
    agent any
    stages {
        stage('stage1') {
            steps {
                sh 'echo Stage1'
                azureDownload storageCredentialId: 'kenchenjenkinsdemotmpl', downloadType: [value: 'container', containerName: 'demo'], includeFilesPattern: '**', downloadDirLoc: 'temp'
                azureUpload storageCredentialId: 'kenchenjenkinsdemotmpl', filesPath: 'temp/**', containerName: 'demo2', virtualPath: env.BUILD_TAG
            }
        }
        stage('stage2') {
            steps {
                sh 'echo Stage2'
            }
        }
        stage('stage3') {
            steps {
                sh 'echo Stage3'
            }
        }
    }
}
