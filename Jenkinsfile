pipeline {
    agent {
        docker {
            image 'sbtscala/scala-sbt:8u332_1.6.2_2.12.15'
            args '-v /root/.sbt:/root/.sbt -u root -w /root -v $PWD:/root'
    }}

    stages {
       
        stage('Compile') {
            steps {
                echo "Compiling..."
                sh "sbt compile"
            }
        }

        stage('Test') {
            steps {
                echo "Testing.."
                sh "sbt test"
            }
        }

        stage('Package') {
            steps {
                echo "Packaging..."
                sh "sbt package"
            }
        }

    }
}
