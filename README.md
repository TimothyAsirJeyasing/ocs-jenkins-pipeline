Jenkins automation scripts for OCS cypress tests

One can use either cypress dashboard or
jenkins pipeline to run the tests in parallel.

However we recommand Jenkins because it does not charge any special fee for any number of test itterations and its high usage in the community.
This script can be directly ported to the Jenkins pipeline by choosing "New Item" in the Jenkins dashboard.

How to run the pipeline jenkins script

Open a new pipeline project in Jenkins and make sure you have added the required plugins like git, pipeline under manage plugins
Select a "New Item" from the dashboard and provide an appropriate name to the job
![image](https://user-images.githubusercontent.com/6670284/143385586-89586789-bdf8-4f86-8f2b-e928bd43f46f.png)
Select the "Pipeline" option from the Items list and press OK button
Now it will open an another page for the job details and the execution script.

Provide an appropriate description
![image](https://user-images.githubusercontent.com/6670284/143384049-fda4a39c-38b7-4ee8-b6e0-6b01a46ef25d.png)

Scroll down and Go to Pipeline under Advanced Project Options
Copy and paste the Jenkinsfile script
![image](https://user-images.githubusercontent.com/6670284/143385377-49ecd003-a214-4973-bffe-a2c8ff5e3fbf.png)

After copying the scipt from the OCS Jenkins Pipeline Repo (https://github.com/TimothyAsirJeyasing/ocs-jenkins-pipeline),
It is required to update the cluster details and the credentials time to time.
The variables BRIDGE_BASE_ADDRESS and BRIDGE_KUBEADMIN_PASSWORD are used in the environment section of the script.
![image](https://user-images.githubusercontent.com/6670284/143384445-e84b4cfb-60f3-4c47-a29d-b3afe97e36ab.png)

Once the parameeters are applied, we can click on Apply and Save buttons.
It will show an another page with an options like Status, Changes, BuildNow, Configure, Delete pipeline and etc.,
![image](https://user-images.githubusercontent.com/6670284/143386999-50ec2a4c-3cbe-415e-8e65-ab74e594a197.png)

Click the Build Now option
![image](https://user-images.githubusercontent.com/6670284/143384673-6bc8c9da-4dad-452c-acf2-ba07e2d9f13b.png)
After clicking the build now option, We can see that the build starts within few second.
By clicking the running build usually appears at the bottom of the left navication, we can go to the buid details page
and can monitor the build execution, log and other details.
