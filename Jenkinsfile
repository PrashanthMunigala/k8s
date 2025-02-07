pipeline {
      agent any
    parameters { choice(name: 'ACTION', choices: ['apply', 'delete'], description: 'select the action to perform')}
    
    stages {

        stage('parameter validation') {
            steps{
                script{
                    if ("${params.PERSON}" == '') {
                        echo "please pass the parameter"
                    } else{
                        echo "the option is selected : ${params.ACTION}"
                    }
                }
            }
        }

        stage('apply') {
            when { expression {
                return params.ACTION == 'apply'
            }
            }
            steps {
                sh 'kubectl apply -f deploy.yaml'
            }
        }
        stage('delete') {
            when { expression {
                return params.ACTION == 'delete'
            }

            }
            steps {
                sh 'kubectl delete -f deploy.yaml'
            }
        }

    }

}
