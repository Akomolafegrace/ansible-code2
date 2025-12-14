pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh  'zip ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
        
            }
        }
        stage('uplaod artifact to jfrog')
        steps{
            sh 'curl -uadmin:APALKYmZCo8dMhFq6cvqwp3mgid -T \
            ansible-${BUILD_ID}.zip \
            "http://18.208.217.40:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
        }


        
    }
}
























