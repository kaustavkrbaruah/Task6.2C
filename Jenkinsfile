pipeline{
    agent any
    environment{
        STAGING_ENV = "SIT753_Staging AWS EC2 instance"
        PROD_ENV = "SIT753_Production AWS EC2 instance"
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
                    emailext to: "$RECIEVER",
                    subject:"Unit and Intergration Tests Successful",
                    attachLog:true

                }
                failure{
                    emailext to: "$RECIEVER",
                    subject: "Unit and Intergration Tests Unsuccessful",
                    attachLog:true

                    
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
                decho "Scanning for Vulnerabilities using Probely"
            }
            post{
            
                success{
                    emailext to: "$RECIEVER",
                    subject:"Security Scan Successful",
                    attachLog:true

                }
                failure{
                    emailext to: "$RECIEVER",
                    subject: "Security Scan Unsuccessful",
                    attachLog:true

                    
                }
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
