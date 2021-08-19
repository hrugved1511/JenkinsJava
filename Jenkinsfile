node{

   
   stage('SCM Checkout'){
     checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '3c9f8f3d-28eb-4468-941c-ea9ba910de67', url: 'https://gitlab.xpanxion.com/Hrugved.Chavan/javaprojectforjenkins.git']]])
   }
   stage ('build')  {
    sh "${mvnHome}/bin/mvn clean install -f MyWebApp/pom.xml"
    }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3.6.3', type: 'maven'   
      
      }

   stage('Deploy to Tomcat'){
     
     deploy adapters: [tomcat9(credentialsId: '73f81183-1ae7-48cc-be64-5d7ed3285fbb', path: '', url: 'http://192.168.1.8:8081')], contextPath: null, war: '**/*.war'
   }
      
}
