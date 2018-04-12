def username = 'jenkins-username'
pipeline {
    agent any
    environment {
        CC = 'clang'
    }
    stages {
        stage('Build') {
            environment {
                DEBUG_FLAGS = '-g'
            }
            steps {
                echo 'Building new branch..'
                echo 'Hello mr ${username}'
                echo "Hello mr ${username}"
                echo "ENV VARIABLES ${env.DEBUG_FLAGS} on ${env.CC}"
                /*
                sh 'make'
                archiveArtifacts artifacts: '/target/*.jar', fingerprint: true
                echo "Build# " + "${env.BUILD_ID}"
                */

            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                echo "Running ${env.DEBUG_FLAGS} on ${env.CC}"
                /* `make check` returns non-zero on test failures,
                 using `true` to allow the Pipeline to continue nonetheless
                sh 'make check || true'
                junit '/target/*.xml'
                */
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                /*
                when {
                  expression {
                    currentBuild.result == null || currentBuild.result == 'SUCCESS'
                  }
                }
                steps {
                    sh 'make publish'
                }
                */
            }
        }
        stage('PostDeploy'){
            steps{
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }

        }
    }
}
