pipeline {
    agent {
        docker {
            image 'maven:3.8.1-adoptopenjdk-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    options {
        skipStagesAfterUnstable()
    }
     stages {
//         stage('Unpack') {
//             steps {
//                 sh 'tar xvzf my-app.tar.gz'
//             }
//         }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
//         stage('Email') { 
//             steps {
//               emailext body: 'The Result is GOOD =)', subject: 'FROM JENKINS', to: 'kasatka5507@yandex.ru'   
//             }
//         }
    }
}
