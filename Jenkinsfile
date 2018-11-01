// 
// With this section of Jenkinsfile commented out, we neeed to have
// Jenkins Kubernetes Pod Template defined in the Jenkins master
//
//podTemplate(label: 'kubernetes',
//  containers: [
//    containerTemplate(name: 'maven', image: 'maven:3.5.2-jdk-8-alpine', ttyEnabled: true, command: 'cat')
//  ]) {
    node("kubernetes") {
      container("maven") {
        stage('Checkout') {
            checkout scm
        }
        stage('Build Test') {
            sh "mvn -Dmaven.test.failure.ignore clean install"
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
      }
    }
  }
//}
