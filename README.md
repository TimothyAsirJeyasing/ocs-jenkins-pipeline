Jenkins automation scripts for OCS cypress tests

One can use either cypress dashboard or
jenkins pipeline to run the tests in parallel.

However we recommand Jenkins because it does not charge any special fee for any number of test itterations and its high usage in the community.
This script can be directly ported to the Jenkins pipeline by choosing "New Item" in the Jenkins dashboard.

How to run the pipeline jenkins script

Open a new pipeline project in Jenkins
     1) Select "New Item"
     
     2) Enter an item name: ocs-jenkins
     3) Select "Pipeline"
     4) Go to Pipeline under Advanced Project Options
     5) Copy and paste the Jenkinsfile script
     6) Apply and Save
Click the Build Now option
