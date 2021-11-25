Jenkins automation scripts for OCS cypress tests

One can use either cypress dashboard or
jenkins pipeline to run the tests in parallel.

However we recommand Jenkins because it does not charge any special fee for any number of test itterations and its high usage in the community.
This script can be directly ported to the Jenkins pipeline by choosing "New Item" in the Jenkins dashboard.

How to run the pipeline jenkins script

Open a new pipeline project in Jenkins

     1) Select "New Item"
     2) Enter an item name: ocs-jenkins
     3) Select "Pipeline"'
          ![image](https://user-images.githubusercontent.com/6670284/143383858-a26a4481-6d46-4bfa-89b2-ebc9e8d7746d.png)
     4) Provide an appropriate description
     ![image](https://user-images.githubusercontent.com/6670284/143384049-fda4a39c-38b7-4ee8-b6e0-6b01a46ef25d.png)

     5) Scroll down and Go to Pipeline under Advanced Project Options
     6) Copy and paste the Jenkinsfile script
     ![image](https://user-images.githubusercontent.com/6670284/143384127-2511d4fc-551a-4ab4-8eec-cfca916898b8.png)
     7) Edit the script and update the cluster details and the credentials under environment section
        Provide the BRIDGE_BASE_ADDRESS=<cluster url>
        and provide the BRIDGE_KUBEADMIN_PASSWORD=<password>
     ![image](https://user-images.githubusercontent.com/6670284/143384445-e84b4cfb-60f3-4c47-a29d-b3afe97e36ab.png)

     6) Apply and Save the script
     
Click the Build Now option
![image](https://user-images.githubusercontent.com/6670284/143384673-6bc8c9da-4dad-452c-acf2-ba07e2d9f13b.png)
We can see that the build starts within few seconds of selecting the Build Now option.
Now if we click the building that might be on that build list at the bottom to the left navication, then we can find all the details related to the build.
