// 
// With this section of Jenkinsfile commented out, we neeed to have
// Jenkins Kubernetes Pod Template defined in the Jenkins master
//
//podTemplate(label: 'kubernetes',
//  containers: [
//    containerTemplate(name: 'maven', image: 'maven:3.5.2-jdk-8-alpine', ttyEnabled: true, command: 'cat')
//  ]) {
    node("ha-pod") {
      container("dind") {
        stage('Checkout') {
            checkout scm
        }
        stage('Build Test') {
            sh """
                export PATH="/opt/maven/apache-maven-3.3.3/bin:/opt/jdk/jdk1.8.0_112/bin:$PATH"
                mvn -Dmaven.test.failure.ignore clean install
            """
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
      }
    }
  }
//}
