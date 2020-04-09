pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
        }
    environment {
       JAVA_HOME = '/usr/lib/jvm/java-8-openjdk-amd64'
        }
    stages {
        //stage('chaos') { 
           // steps {
                //withPythonEnv('/usr/bin/python3.6') {
                // Creates the virtualenv before proceeding
                 //   sh 'pip install chaostoolkit'
                 //   sh 'chaos --version'
                 //   sh 'pip install -U chaostoolkit-spring'
                   // }
              //  }
           // }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
                 withPythonEnv('/usr/bin/python3.66') {
                // Creates the virtualenv before proceeding
                    sh 'chaos --version'
                    }
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
    }
}
