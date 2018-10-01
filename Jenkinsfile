pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "building..."'
        sleep 1
        sh 'echo "build successful."'
      }
    }
    stage('Test') {
      parallel {
        stage('Unit Tests') {
          steps {
            sh 'echo "Running unit tests..."'
            sleep 1
            sh 'echo "Unit tests successfully run."'
          }
        }
        stage('Integration Tests') {
          steps {
            sh 'echo "Running integration tests..."'
            sh 'echo "Integration tests successfully run."'
            sleep 1
          }
        }
      }
    }
    stage('Publish SNAPSHOT to Artifact') {
      when {
        branch 'dev'
      }
      steps {
        sh 'echo "Publishing to artifact"'
        sleep 1
      }
    }
    stage('Publish RC to Artifact') {
      when {
        branch 'release/*'
      }
      steps {
        sh 'echo "Publishing to artifact"'
        sleep 1
      }
    }
    stage('Publish RELEASE to Artifact') {
      when {
        branch 'master'
      }
      steps {
        sh 'echo "Publishing to artifact"'
        sleep 1
      }
    }
  }
  options {
    disableConcurrentBuilds()
  }
}
