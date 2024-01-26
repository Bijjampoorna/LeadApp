pipeline{
    agent{label 'Linux-Node'}
    
      stages {
          stage('clean'){
              tools{
                  maven 'maven 3.9.5'
              }
              steps {
                  sh 'mvn -version'
                  sh "mvn test"
              }
              
            stage('test'){
                tools {
                    maven 'maven 3.9.5'
                }
                steps {
                    sh 'mvn -version'
                    sh "mvn test"
                }
            }  
            stage('package'){
                tools {
                    maven 'maven 3.9.5'
                }
                steps {
                    sh 'mvn -version'
                    sh "mvn package"
                }
                
            }
            stage('deployment'){
                deploy adapters: [tomcat9(credentialsId: 'tomcat',path: '',url: 'http://13.201.38.188:8080/')],contextPath: 'LeadApp',war: '/target/*.war'
            }
          }
          
          
      }
    
}