pipeline {
  agent any

  parameters {
    booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests?')
    string(name: 'DEPLOY_ENV', defaultValue: 'staging', description: 'Deploy target')
  }

  environment {
    MY_VAR = "lab12"
    NODE_VERSION = "14.20.0"
  }

  tools {
    // Only works if these exist in Jenkins -> Global Tool Configuration
    jdk 'jdk11'
    maven 'Maven-3.8.8'
  }

  stages {

    stage('Build') {
      steps {
        echo "Building... ENV: ${MY_VAR}"
      }
    }

    stage('Test') {
      when {
        expression { return params.RUN_TESTS == true }
      }
      steps {
        echo "Running tests..."
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploying to ${params.DEPLOY_ENV}"
      }
    }
  }

  post {
    success { echo "BUILD SUCCESS" }
    failure { echo "BUILD FAILED" }
    always  { echo "Cleanup / Always Executed" }
  }
}
