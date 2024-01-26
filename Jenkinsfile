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
                deploy adapters: [tomcat9(credentialsId: 'Tomcat_Credentials',path: '',url: 'http://15.206.80.117:8080/')],contextPath: 'Pipeline_LeadApp',war: '**/*.war'
                }
            }
          }
           post {
		success {
		          	echo 'job was built successfully'
		        }
		failure {
			        echo 'job was not build..it was failed'
		        }
	        }
          
      }
    

