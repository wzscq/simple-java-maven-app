pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
    		def remote = [:]
		    remote.name = 'test'
		    remote.host = '47.89.245.19'
		    remote.user = 'root'
		    remote.password = '2Gb6g99dq5'
		    remote.allowAnyHosts = true
		    stage('Remote SSH') {
      		sshCommand remote: remote, command: "ls -lrt"
      		sshCommand remote: remote, command: "for i in {1..5}; do echo -n \"Loop \$i \"; date ; sleep 1; done"
    		}
        
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}