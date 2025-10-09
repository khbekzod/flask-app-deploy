template = '''
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: kubernetes
  name: kubernetes
spec:
  serviceAccount: kubernetes
  containers:
  - image: kubernetes
    name: kubernetes
    '''

podTemplate(cloud: 'kubernetes', label: 'kubernetes', yaml: template) {
node("kubernetes") {
    container("kubernetes") {
    stage ("Checkout SCM") {
        git branch: 'main', url: 'https://github.com/khbekzod/flask-app-deploy.git'
    }

    stage("Check") {
        sh """
        terraform version
        helm version
        kubectl version
        kubectl get nodes
        """
    }
    }
}
}