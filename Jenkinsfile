pipeline {
    agent any

    parameters {
        booleanParam(name: "RUN_INTEGRATION_TESTS", defaultValue: true)
    }

    stages {
        stage('Test') {
            parallel {
                stage('Unit tests') {
                    when {
                        expression { return params.RUN_INTEGRATION_TESTS }
                    }
                    steps {
                        sh './mvnw test -D testGroups=unit -f shopping-cart-v2/pom.xml'
                    }
                }
            }
        }
    }
}
