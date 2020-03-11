pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                sh '''
                    "chmod 777 ./fakeScript.sh"
                    "chmod 777 ./health-check.sh"
                '''
                retry(3){
                    sh "./fakeScript.sh"
                }
                
                timeout(time:1, unit:'MINUTES'){
                    sh "./health-check.sh"
                }
            }
        }
    }
}
