pipeline {
  agent any
  stages {
    stage ("Build") {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('pmd') {
      steps {
        sh 'mvn pmd:pmd'
      }
    }
    stage('Generate Sure-fire Report') {
      steps {
        sh 'mvn surefire-report:report'
      }
      post {
        success {
          archiveArtifacts artifacts: '**/target/site/surefire-report.html', fingerprint: true
        }
      }
    }
    stage('Generate Javadoc') {
      steps {
        sh 'mvn javadoc:jar'
      }
      post {
        success {
          archiveArtifacts artifacts: '**/target/site/apidocs/**', fingerprint: true
        }
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
    }
  }
}
