pipeline{
  agent any
  environment{
    NEW_VERSION = '1.3.0'
  }
  parameters{
    string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
    choice(name: 'VERSION', choices: ['1.1.0', '1.2.0'], description: '')
    booleanParam(name: 'executetests', defaultValue: 'true', description: '')
  }
  stages{
    stage("build")
    {
      steps{
        echo 'Building the application...'
        echo "Building version ${env.NEW_VERSION}"
      }
    }
    
    stage("test")
    {
      when{
        expression{
          params.executetests
        }
      }
      steps{
        echo 'Testing the application...'
      }
    }
    
    stage("deploy")
    {
      steps{
        echo 'Deploying the application...'
        echo "Deploying version ${params.VERSION}"
      }
    }
  }
}  
