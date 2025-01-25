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
        sh "echo branch- ${params.BRANCH_NAME},sleeptime - ${params.SLEEP_TIME}, port- ${params.PORT}"
      }
    }
       stage('build'){
      steps{
        sh 'mvn clean package -DSkipTests=True'
        archiveArtifacts artifacts: 'target/hello-demo-*.jar', followSymlinks: false
        
      }
    }
     stage('test'){
      steps{
        sh 'mvn test'
        junit keepTestNames: true, stdioRetention: '', testResults: 'target/surefire-reports/TEST-*.xml'
        
      }
    }

    
    stage('Local Deployment'){
      steps{
        sh """ java -jar /target/hello-demo-*.jar > /dev/null& """
      }
    }

      
    stage('Unit Testing'){
      steps{
       sh 'sleep ${params.SLEEP_TIME}'
       sh 'curl -s http://localhost:${params.PORT}/hello'

      }
    }

      
    
  }
}
