node{

   
   stage('SCM Checkout'){
     git 'https://github.com/sivajavatechie/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3.6.3', type: 'maven'   
      
      }

   stage('Deploy to Tomcat'){
     
     deploy adapters: [tomcat9(credentialsId: '73f81183-1ae7-48cc-be64-5d7ed3285fbb', path: '', url: 'http://192.168.1.8:8080')], contextPath: null, war: '**/*.war'
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         sh "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
