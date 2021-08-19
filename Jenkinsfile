node{

   def tomcatWeb = '\\var\\lib\\tomcat9\\webapps'
   def tomcatBin = '\\var\\lib\\tomcat9\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://gitlab.xpanxion.com/Hrugved.Chavan/javaprojectforjenkins.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3.6.3', type: 'maven'   
      
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     /*sh "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""*/
     deploy adapters: [tomcat9(credentialsId: '73f81183-1ae7-48cc-be64-5d7ed3285fbb', path: '', url: 'http://192.168.1.8:8080')], contextPath: null, war: '**/*.war'
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         sh "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
