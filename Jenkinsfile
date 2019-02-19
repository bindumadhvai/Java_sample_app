node {
  stage('HelloWorld') {
    echo 'Hello World'
  }
  
  stage('Docker Build') {
    sh """
       sudo docker build -t bindumadhavikura/k8:${BUILD_NUMBER} /var/lib/jenkins/k8
       sudo docker push bindumadhavikura/k8:${BUILD_NUMBER}
    """
  }

  stage('pods') {
    sh """
       sudo kubectl set image deployment/jen-app jen-app=bindumadhavikura/k8:${BUILD_NUMBER} --insecure-skip-tls-verify=true
    """
  }
}
