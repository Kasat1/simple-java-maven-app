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
        stage('Unpack') {
            steps {
                sh 'echo '$build_number_auto'
                sh 'tar xvzf $J_HOME/artifacts/my-app-37.tar.gz --directory $J_HOME/artifacts/'
            }
        }
//         stage('Test') {
//             steps {
//                 sh 'mvn test'
//             }
//             post {
//                 always {
//                     junit 'target/surefire-reports/*.xml'
//                 }
//             }
//         }
        stage('Deliver') { 
            steps {
                sh 'java -jar $J_HOME/artifacts/target/my-app-1.0-SNAPSHOT.jar' 
            }
        }
//         stage('Email') { 
//             steps {
//               emailext body: 'The Result is GOOD =)', subject: 'FROM JENKINS', to: 'kasatka5507@yandex.ru'   
//             }
//         }
    }
}
