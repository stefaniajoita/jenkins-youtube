
def gv
pipeline{
  agent any
  environment{
    NEW_VERSION = '1.3.0'
  }
  parameters{
    choice(name: 'VERSION', choices: ['1.1.0', '1.2.0'], description: '')
    booleanParam(name: 'executetests', defaultValue: 'true', description: '')
  }
  stages{
        stage("init")
    {
      steps{
        script{
          gv = load "script.groovy"
        }
      }
    }
    
    stage("build")
    {
      steps{
        script{
         gv.buildApp()
       }
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
