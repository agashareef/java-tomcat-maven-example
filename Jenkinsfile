node{
      def mvnHome = tool name: 'maven 3.6.3', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
            sshagent(['7d3f18c1-23ce-4f4d-9dea-5eb847a6bfd8']) {
               sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@52.87.194.232:/opt/tomcat/webapps'
              
          }
         
     }
      
 }
