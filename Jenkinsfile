pipeline {
    agent any
    stages { 
        
            steps {
                git " url: https://github.com/Jagadeeshcap/testsamplerepo.git"
                echo 'Hello World'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
