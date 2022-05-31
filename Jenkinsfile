pipeline {
    agent {
        docker {
            image 'mozilla/sbt:latest'
            args '-v /root/.ivy2:/root/.ivy2 -v /root/.sbt:/root/.sbt -v $PWD:/app -w /app'
            //args '-v /root/.ivy2:/root/.ivy2 -v /root/.sbt:/root/.sbt -u sbtuser -w /home/sbtuser -v $PWD:/home/sbtuser'
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
