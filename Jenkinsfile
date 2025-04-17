pipeline{
    agent any
     tools{
      maven 'M2_HOME'
           }
      stages{
      stage('Git checkout'){
          steps {
            echo 'this is for cloning git repo'
            git 'https://github.com/ArunTvv/star-agile-health-care.git'
          }
        }
         stage('Maven package'){
          steps {
            echo 'this is for packaging the application'
            sh 'mvn package'
          }
        }
         stage('Test Results'){
          steps {
            echo 'this is for generating test Results'
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, icon: '', keepAll: false, reportDir: '/var/lib/jenkins/workspace/HealthCare/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
          }
        }
          stage('Docker image creation'){
          steps {
            echo 'this is for Docker image build'
              sh 'docker build -t aruntvv/healthcarenew:latest .'
          }
        }
      }
}
