node{
    stage("code checkout"){
        git 'https://github.com/Ranjana1984/capstone-bank.git'
    }
    stage("code build"){
        sh "mvn clean package"
    }
    stage("docker images"){
        sh "docker build -t ranjana23/banking-project:1.0 ."
    }
    stage("login and images push"){
        withCredentials([string(credentialsId: 'dockerlogin', variable: 'dockerlogin')]) {
            sh "docker login -u ranjana23 -p ${dockerlogin}"
            sh "docker push ranjana23/banking-project:1.0"
        }
    }
}
