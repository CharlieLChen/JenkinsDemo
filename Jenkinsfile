pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                retry(3){
                    sh "./fakeScript.sh"
                }
                
                timeout(time:3, unit:'MINUTES'){
                    sh "./health-check.sh"
                }
            }
        }
       post{
                    always{
                        sh "echo always"
                    }
                    success {
                        sh "echo success"
                    }
                    failure {
                        sh "echo failed"
                    }
                    changed {
                         echo 'This will run only if the state of the Pipeline has changed'
                         echo 'For example, if the Pipeline was previously failing but is now successful'
                    }
                }
        
    }
}
