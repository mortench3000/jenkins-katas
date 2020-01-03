pipeline {
  agent {
    label 'general-purpose'
  }
  stages {
    stage('Parallel execution') {
      parallel {
        stage('say hello') {
          steps {
            sh 'echo "hello Jenkins world"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
          }
        }

      }
    }

  }
}