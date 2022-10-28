pipeline {
  agent any
  
  stages {
      stage("GIT CHECKOUT") {
            steps {
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/Zeroxcharisma/CI-CD.git'
            }
        }
        stage('MVN CLEAN') {
      steps {
        sh 'mvn clean '
      }
    }
    stage('MVN COMPILE') {
      steps {
            sh 'mvn compile '
      }
    }
    
       stage('MVN TEST') {
         steps {
               sh 'mvn test'
            }
        }
       stage("Maven BUILD") {
            steps {
                script {
                    sh "mvn install -DskipTests=true"
                }
            }
        }

       stage ('Maven Test Sonar') {
            steps {
 sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:RELEASE:sonar -Dsonar.login=admin -Dsonar.password=sonar'
           }
}
stage('MVN DEPLOY') {
      steps {
            sh 'mvn deploy -DskipTests=true '
      }
    }
  

    




}



}
