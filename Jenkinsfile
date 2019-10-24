node {
   
   stage('Code Checkout') { // for display purposes
    git credentialsId: 'maven', url: 'https://github.com/atulpro-org/maven-pro.git'  
   }
   stage('Code Build') {
    withMaven(jdk: 'JDK.1.8.0_222', maven: 'maven') {
     sh 'mvn clean compile'
    }  
   }
   stage('Unit Test') {
       withMaven(jdk: 'JDK.1.8.0_222', maven: 'maven') {
        sh 'mvn test'
     }  
   }
   stage('SonarQube Analysis') {
       withMaven(jdk: 'JDK.1.8.0_222', maven: 'maven') {
       sh 'mvn verify sonar:sonar \
          -Dsonar.projectKey=atulpro-org.maven-example \
          -Dsonar.organization=itrainwo \
          -Dsonar.host.url=https://sonarcloud.io \
          -Dsonar.login=3fdeef44dc2f1eb8e4573c46a06616cfd4a85605'
       }
   } 
   stage('Archive to Jfrog') {
   } 
   stage('Docker Image') {
   } 
   stage('Deploy to Prods') {
   } 
}
