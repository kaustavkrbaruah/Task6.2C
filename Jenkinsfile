pipeline{
    agent any
    environment{
        STAGING_ENV = "SIT753_Staging AWS EC2 instance"
        PROD_ENV = "SIT753_Producation AWS EC2 instance"
        RECIEVER = "kaustavkrbaruah@gmail.com"

    }
    stages{
        stage("Build"){
            steps{
                echo "Building code using PyInstaller"
            }
    
        }
        stage("Unit and Integration Tests"){
            steps{
                echo "Running Unit and Integration tests using PyTest"
            }
            post{
            
                success{
                    mail to: "$RECIEVER",
                    subject:"Tests Successful",
                    attachLog: true

                }
                failure{
                    mail to: "$RECIEVER",
                    subject: "Tests Unsuccessful",
                    attachLog: true
                    
                }
            }
        }
        stage("Code Analysis"){
            steps{
                echo "Analysing code using FindBugs"
            }
            
        }
        stage("Security Scan"){
            steps{
                echo "Scanning for Vulnerabilities using Probely"
            }
            
        }
        stage("Deploy to Staging"){
            steps{
                echo "Deploying application to $STAGING_ENV"
            }
            
        }
        stage("Integration Tests on Staging"){
            steps{
                echo "Running integration test using AWS Device Farm"
            }
            
        }
        stage("Deploy to Production"){
            steps{
                echo "Deploying applicaiton to $PROD_ENV"
            }
            
        }
        
    }
    
 }
