pipeline {
    agent {
        docker {
            image 'sbtscala/scala-sbt:8u332_1.6.2_2.12.15'
            //args '-v /root/.ivy2:/root/.ivy2 -v /root/.sbt:/root/.sbt -v $PWD:/app -w /app'
            //args '-v /root/.ivy2:/root/.ivy2 -v /root/.sbt:/root/.sbt -u sbtuser -w /home/sbtuser -v $PWD:/home/sbtuser'
            args '-v /root/.sbt:/root/.sbt -u sbtuser -w /home/sbtuser -v $PWD:/home/sbtuser'
    }}

    stages {
        
       stage('Changing directory') {
            steps {
                echo "Changing directory..."
                sh "cd /home/sbtuser"
                sh "ls -al"
            }
        }
       
        stage('Debug') {
            steps {
                echo "Debuging..."
                sh "echo $PWD"
                sh "whoami"
                sh "ls -al"
            }
        }

        stage('Compile') {
            steps {
                echo "Compiling..."
                sh "cd /home/sbtuser"
                sh "sbt compile --batch -Dsbt.server.forcestart=true"
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
