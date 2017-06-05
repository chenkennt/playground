pipeline {
    agent any
    stages {
        stage('stage1') {
            steps {
                sh 'echo Stage1'
                azureDownload storageCredentialId: 'kenchenjenkinsdemotmpl', downloadType: [value: 'container', containerName: 'demo'], includeFilesPattern: '**', downloadDirLoc: 'temp'
                azureUpload 'kenchenjenkinsdemotmpl', 'temp/**', 'demo2'
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
