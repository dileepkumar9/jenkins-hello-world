pipeline
{
  agent any
  tools{
    maven 'maven399'
  }
  stages
  {
    stage('print'){
      steps{
        sh 'echo maven version'
        sh 'mvn -v'
      }
    }
       stage('build'){
      steps{
        sh 'mvn clean package -DSkipTests=True'
        archiveArtifacts artifacts: '/target/hello-demo-*.jar', followSymlinks: false
        
      }
    }
     stage('test'){
      steps{
        sh 'mvn test'
        junit keepTestNames: true, stdioRetention: '', testResults: '/target/surefire-reports/TEST-*.xml'
        
      }
    }
      
    
  }
}
