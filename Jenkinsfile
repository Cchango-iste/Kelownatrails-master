pipeline{
    agent any
    environment {
    //FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    TOKENAWS = credentials('ssh-production-key')
    }

 stages{
        stage('Building'){
            steps{
           // sh 'npm install -g firebase-tools'
                echo 'Biulding...'
            }
        } 
        stage('Testing Environment'){
            steps{
            //sh 'firebase deploy -P testing-enviroment-7fcc7 --token "$FIREBASE_DEPLOY_TOKEN"'
            //input message: 'After testing. Do you want to continue with Staging Environment? (Click "Proceed" to continue)'
            sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@44.202.152.59 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html/; sudo git clone https://github.com/Cchango-iste/Kelownatrails-master.git /var/www/html"'
            }
        } 
        stage('Staging Environment'){
            steps{
             //sh 'firebase deploy -P staging-enviroment-7b133 --token "$FIREBASE_DEPLOY_TOKEN"'
             sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@3.80.233.73 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html/; sudo git clone https://github.com/Cchango-iste/Kelownatrails-master.git /var/www/html"'
            }
        } 
        stage('Production Environment'){
            steps{
            //sh 'firebase deploy -P production-38156 --token "$FIREBASE_DEPLOY_TOKEN"'
             sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@34.204.79.179 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html/; sudo git clone https://github.com/Cchango-iste/Kelownatrails-master.git /var/www/html"'
            }
        } 
    }

}
