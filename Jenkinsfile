node('linux'){
    stage('Build'){
        git 'https://github.com/codeistheway/java-project.git'
        sh "ant -f build.xml -v"
    }
    
    stage('Deploy'){
        sh "aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://seis665spring19-assignment10/"
    }
    
    stage('Unit Tests'){
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'AWS user for Jenkins', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
            sh "aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins"
        }
        
    }
}
