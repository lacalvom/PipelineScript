pipeline {
    agent any
    stages {
        stage('Git-Checkout'){
            steps {
                echo "Checking Out from Git Repo";
                git branch: 'main', url: 'https://github.com/lacalvom/PipelineScript.git'
            }
        }

        stage ('Build') {
            steps {
                echo "Building the Checked-Out project!";
                sh 'bash Build.sh'
            }
        }

        stage ('Unit-Test') {
            steps {
                echo "Running JUnit Test";
                /*sh exit ("1");*/
                sh 'bash Unit.sh'
            }
        }

        stage ('Quality-Gate') {
            steps {
                echo "Verifying Quality Gates";
                sh 'bash Quality.sh'
            }
        }
        
        stage ('Deploy') {
            steps {
                echo "Pass!";
                sh 'bash Deploy.sh'
            }
        }
        
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
