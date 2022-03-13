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
                sh 'cp target/my-app-1.0-SNAPSHOT.jar $J_HOME/artifacts/my-app-$build_number_auto.jar'
            }
        }
        stage('Create_Archive') { 
            steps {
                sh 'tar czf $J_HOME/artifacts/my-app-$build_number_auto.tar.gz target/my-app-1.0-SNAPSHOT.jar' 
                sh 'echo $qwe'
            }            
        }
    }
    post{
        success {
        echo "trigger adhoc pipline"
        build job: 'adhoc', parameters: 
            [string(name: 'build_number_auto', value: '$qwe')]
        }
    }
}
