pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh  'rm -rf *.zip || echo""'
                sh  'zip -r ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
        
            }
        }
        stage('uplaod artifact to jfrog'){
            steps{
            sh 'curl -uadmin:APALKYmZCo8dMhFq6cvqwp3mgid -T \
            ansible-${BUILD_ID}.zip \
            "http://18.208.217.40:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
        }

        }
        stage('publish to ansible server'){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'AnsibleServer', \
                transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: \
                'ls', execTimeout: 120000, flatten: false, makeEmptyDirs: false, \
                noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: \
                '.', remoteDirectorySDF: false, removePrefix: '', \
                sourceFiles: 'ansible-${BUILD_ID}.zip')], usePromotionTimestamp: false, \
                useWorkspaceInPromotion: false, verbose: false)]) 
            }
        }
        

        
    }
}
























