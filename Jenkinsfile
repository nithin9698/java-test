pipeline {
    agent any

    environment {
        function_name = 'myfunctionjava'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Builds'
                sh 'mvn package'
            }
        }
        
        stage("sonarQube analysis") {
            steps {
                withSonarQubeEnv('Sonar') {
                    echo 'scanning'
                    sh 'mvn sonar:sonar'
                }
            }
        }
        // stage('Push') {
        //     steps {
        //         echo 'Push'

        //         sh "aws s3 cp target/sample-1.0.3.jar s3://javabucketvineet"
        //     }
        // }

        // stage('Deploy') {
        //     steps {
        //         echo 'Build'

        //         sh "aws lambda update-function-code --function-name $function_name --region us-east-2 --s3-bucket javabucketvineet --s3-key sample-1.0.3.jar"
        //     }
       // }
    }
}