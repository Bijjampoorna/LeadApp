pipeline{
    agent{label 'Linux-Node'}
    
      stages {
          stage('clean'){
              tools{
                  maven 'maven_3.9.5'
              }
              steps {
                  sh 'mvn -version'
                  sh "mvn test"
              }
          }
              
            stage('test'){
                tools {
                    maven 'maven_3.9.5'
                }
                steps {
                    sh 'mvn -version'
                    sh "mvn test"
                }
            }  
            stage('package'){
                tools {
                    maven 'maven_3.9.5'
                }
                steps {
                    sh 'mvn -version'
                    sh "mvn package"
                }
                
            }
            stage('deployment'){
                steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat',path: '',url: 'http://15.206.80.117:8080/')],contextPath: 'LeadApp',war: '**/*.war'
                }
            }
          }
          
          
      }
    

