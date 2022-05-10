pipeline {
    agent none
    stages {
	    stage('Non-Parallel Stage') {
	        agent {
                label "master"
            }
            steps {
                echo 'This stage will be executed first'
            }
        }
        stage('Run Tests') {
            parallel {
                stage('Test On Linux') {
                    agent {
                        label "Jenkins_Linux_Node"
                    }
                    steps {
                        echo "Task1 on Agent"
                    }
                }
                stage('Test On Master') {
                    agent {
                        label "master of the universe"
                    }
                    steps {
    				    echo "Task1 on Master"
	    		    }
                }
            }
        }
    }
}
