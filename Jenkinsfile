pipeline { 
    agent any 
    stages { 
        stage('Build') { 
            steps { 
                echo "Build Docker Image" 
                bat "docker build -t kubedemo:v1 ." 
            } 
        } 
        stage('Docker login') { 
            steps { 
                bat "docker login -u satya1306 -p satyalasya06" 
            } 
        }
        stage('Push docker image to hub') { 
            steps { 
                echo "push docker image to docker hub"
                bat "docker tag kubedemo:v1 satya1306/gowri62:week9"
                bat "docker push satya1306/gowri62:week9" 
            } 
        }
        stage('Deploy to Kubernetes') { 
            steps { 
                bat "kubectl apply -f deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml" 
            } 
        } 
    } 
    post { 
        success { 
            echo 'Pipeline completed successfully!' 
        } 
        failure { 
            echo 'Pipeline failed. Please check the logs.' 
        } 
    } 
} 
