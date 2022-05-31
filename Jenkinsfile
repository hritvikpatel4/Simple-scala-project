pipeline {
    agent {
        docker {
            image 'sbtscala/scala-sbt:17.0.2_1.6.2_3.1.2'
            // args '-v ~/.ivy2:/root/.ivy2 -v ~/.sbt:/root/.sbt -v $PWD:/app -w /app'
            args '-u sbtuser -w /home/sbtuser'
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
                echo "Testing..."
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
