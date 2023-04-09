pipeline {
    agent any 
    stages {
        stage('Compile and Clean') { 
            steps {

                echo "mvn clean compile"
            }
        }
        stage('Test') { 
            steps {
                echo "mvn test "
            }
        }
        stage('Deploy') { 
            steps {
                echo "mvn package"
            }
        }
    }
}
