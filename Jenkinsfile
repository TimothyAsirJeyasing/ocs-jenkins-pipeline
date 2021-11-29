pipeline {
  agent {
    docker {
      image 'cypress/base:14.17.0'
      args '-u root:sudo -v $HOME/workspace/myproject:/myproject'
    }
  }
  parameters{
        string(name: 'Cluster', defaultValue: 'https://console-openshift-console.apps.bot-d81a1453-4ed0-4117-aeaa-d88316e69597.devcluster.openshift.com', description: "Enter the cluster url")
        string(name: 'Password', defaultValue: '23sadfasf23fdsa', description: "Please provide the kubeadmin password")
        string(name: 'CypressPRID', defaultValue: '', description: "Please provide your cypress dashboard project id if available or keep blank this field")
  }

    stages {
     stage('build-environment') {
      steps {
        sh 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" | tee -a /etc/apt/sources.list'
        sh 'wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
        sh '''apt-get update -y'''
        echo "We can skip clone the repo if we are using jenkins multi-pipline source"
        git 'https://github.com/openshift/console'
        echo "Installing the required packages"
        sh '''apt-get install -y libgtk2.0-0 google-chrome-stable libgtk-3-0 libgbm-dev libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2 libxtst6 xauth xvfb'''
        sh 'cd frontend && yarn install'
        echo "The following installation required to fix Cypress binary missing issue"
        sh './frontend/node_modules/.bin/cypress install --force'
      }
    }
    stage('cypress parallel tests') {
      environment {
	      BRIDGE_BASE_ADDRESS="${Cluster}"
	      BRIDGE_KUBEADMIN_PASSWORD="${Password}"
	      CYPRESS_PROJECT_ID="${CypressPRID}"
      }
      parallel {
          // TODO: Loop over the parallel directory and execute the tests in parallel
	  // TODO: Loop over the normal directory and execute the tests one by one
	  // Some tests can not be executed in parallel.y
          stage('Test Add Capacity') {
          steps {
            echo "Running build ${env.BUILD_ID} using the cluster: ${Cluster}"
            sh 'cd frontend/packages/ceph-storage-plugin/integration-tests-cypress && node --max-old-space-size=4096 ../../../node_modules/.bin/cypress run --config-file cypress-ceph.json --env openshift=true --browser ${BRIDGE_E2E_BROWSER_NAME:=chrome} --headless --spec tests/add-capacity.spec.ts'
          }
        }
        stage('Test Block Pool') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh 'cd frontend/packages/ceph-storage-plugin/integration-tests-cypress && node --max-old-space-size=4096 ../../../node_modules/.bin/cypress run --config-file cypress-ceph.json --env openshift=true --browser ${BRIDGE_E2E_BROWSER_NAME:=chrome} --headless --spec "tests/block-pool-create.spec.ts,tests/block-pool-delete.spec.ts,tests/block-pool-update.spec.ts"'
          }
        }
        stage('Test Bucket Class') {
          steps {
            echo "Running build ${env.BUILD_ID}"
            sh 'cd frontend/packages/ceph-storage-plugin/integration-tests-cypress && node --max-old-space-size=4096 ../../../node_modules/.bin/cypress run --config-file cypress-ceph.json --env openshift=true --browser ${BRIDGE_E2E_BROWSER_NAME:=chrome} --headless --spec tests/bucket-class-spec.ts'
          }
        }

          } // Parallel
    } // Stage
  } // Stages
     post {
    always {
            echo "Run Report"
              publishHTML (target: [
      allowMissing: false,
      alwaysLinkToLastBuild: false,
      keepAll: true,
      reportDir: 'frontend/gui_test_screenshots/',
      reportFiles: 'cypress_report_ceph.html',
      reportName: "OCS Test Report"
    ])
    } // always
   } // post
}
