node 
{
   def mvnHome
   stage('Preparation') 
   { 
      git 'https://github.com/gyayakjain/Java.git'          
      MAVEN_HOME = tool 'MAVEN_HOME'
      jdk    = tool name: 'JAVA8'
      env.JAVA_HOME = "${jdk}"
   }
   stage('Build') 
   {
      if (isUnix()) 
      {
         sh "'${MAVEN_HOME}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else 
      {
         bat(/"${MAVEN_HOME}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   //stage('Results') 
   //{
    //  junit '**/target/surefire-reports/TEST-*.xml'
     // archive 'target/*.jar'
   //}
   stage ('Clone') 
   {
        git url: 'https://github.com/gyayakjain/Java.git'
    }
 
   /* stage ('Artifactory configuration') 
   {
        mvnHome = tool 'mavenhome'
        rtMaven.tool = 'mavenhome' // Tool name from Jenkins configuration
        rtMaven.deployer releaseRepo: 'libs-release-local', snapshotRepo: 'libs-snapshot-local', server: server
        rtMaven.resolver releaseRepo: 'libs-release', snapshotRepo: 'libs-snapshot', server: server
        buildInfo = Artifactory.newBuildInfo()
        buildInfo.env.capture = true
    }
 
    stage ('Exec Maven') 
   {
        rtMaven.run pom: 'pom.xml', goals: 'clean install', buildInfo: buildInfo
    }*/

}
