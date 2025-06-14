pipeline {
    agent {
        node {
            label "maven"
        }
    }
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {
        //Artifactory create
        stage('build') {
            steps {
                sh 'mvn clean deploy' //-Dmaven.test.skip=true
            }
        }
        //docker image build
        stage('image build') {
            steps {
                sh 'docker build -t devopssteps/myapp:latest .'
            }
        }
    }
}

