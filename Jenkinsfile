node(build-slave) {
   stage('Preparation') {
      git 'https://github.com/gunesmes/code-run-test-automation-ci.git'
   }
   stage('Build') {
       sh 'cd /var/jenkins_home/workspace/testhive/app'
       sh 'docker-compose up'
   }
   stage('Unit Test') {
       sh 'cd /var/jenkins_home/workspace/testhive/app/src/test'
       sh 'bash run_unit_tests.sh'
   }
   stage('Service Test') {
       sh 'cd /var/jenkins_home/workspace/testhive/service-test' 
       sh 'bash service_tests.sh'
   }
   stage('UI Test') {
       sh 'cd /var/jenkins_home/workspace/testhive/web-automation'
       sh 'bash run_web_automation.sh'
   }
   stage('Test Deployment') {
   		 sh 'echo live deployment started'
   }
   stage('Performance Test') {
       sh 'bash run_performance_test.sh'
   }
   stage('Live Deployment') {
   		 sh 'echo test deployment started'
   }
}
