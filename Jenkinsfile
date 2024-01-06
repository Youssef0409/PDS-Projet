pipeline {
    agent any 
    tools { 
        maven 'maven'
        nodejs 'node'
    }
    stages {
        stage ("Clean up"){
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo"){
            steps {
                sh "git clone https://github.com/Youssef0409/PDS-Projet.git"
            }
        }
        stage ("Generate frontend image") {
            steps {
                 dir("PDS-Projet/PdsFront"){
                    sh "docker build -t front ."
                }                
            }
        }
        stage ("Generate backend image") {
              steps {
                   dir("PDS-Projet/PdsBackend"){
                      sh "mvn clean install"
                      sh "docker build -t back ."
                  }                
              }
          }
        stage ("Run docker compose") {
            steps {
                 dir("PDS-Projet"){
                    sh " docker compose up -d"
                }                
            }
        }
    }
}
