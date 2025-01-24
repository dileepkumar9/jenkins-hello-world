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
        
      }
    }
     stage('test'){
      steps{
        sh 'mvn test'
        
      }
    }
      
    
  }
}
