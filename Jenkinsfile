pipeline {
    agent {
        docker {
            image 'sbtscala/scala-sbt:8u332_1.6.2_2.12.15'
            // args '-v ~/.ivy2:/root/.ivy2 -v ~/.sbt:/root/.sbt -v $PWD:/app -w /app'
    }}

    stages {

        stage('Compile') {
            steps {
                echo "Compiling..."
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt compile"
            }
        }

        stage('Test') {
            steps {
                echo "Testing..."
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt test"
            }
        }

        stage('Package') {
            steps {
                echo "Packaging..."
                sh "${tool name: 'sbt', type: 'org.jvnet.hudson.plugins.SbtPluginBuilder$SbtInstallation'}/bin/sbt package"
            }
        }

    }
}
