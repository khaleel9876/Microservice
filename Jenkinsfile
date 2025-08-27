pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'shaik', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B18615BBD34ADF0F943CCED2ACF5DB95.gr7.us-east-1.eks.amazonaws.com']]) {
                 sh "kubectl apply -f deployment-service.yml"
                 sleep 60
                }
            }
        }
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'shaik', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B18615BBD34ADF0F943CCED2ACF5DB95.gr7.us-east-1.eks.amazonaws.com']]) {
                  sh "kubectl get svc -n webapps"
                    }
            }
        }
    }
}
