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
        stage('Build_jar_file') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Create_Archive') { 
            steps {
                sh 'tar czf $J_HOME/artifacts/my-app-$build_number_auto.tar.gz target/my-app-1.0-SNAPSHOT.jar' 
            }            
        }
        stage('Create_Archive12') { 
            steps {
                sh 'echo $J_HOME' 
            }            
        }
    }
}
// /var/jenkins_home/artifacts
