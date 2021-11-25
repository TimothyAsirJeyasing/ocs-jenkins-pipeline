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

After copying the script from the OCS Jenkins Pipeline Repo (https://github.com/TimothyAsirJeyasing/ocs-jenkins-pipeline),
The variables BRIDGE_BASE_ADDRESS and BRIDGE_KUBEADMIN_PASSWORD are used in the environment section of the script.
These values will be used at the run time. This values can be passed as a parameters during the build.
![image](https://user-images.githubusercontent.com/6670284/143384445-e84b4cfb-60f3-4c47-a29d-b3afe97e36ab.png)

Once the script is copied we can click on Apply and Save buttons.
It will display an another page which contains options like Status, Changes, BuildNow, Configure, Delete pipeline and etc.,
![image](https://user-images.githubusercontent.com/6670284/143460228-9f98eac9-0fa8-40aa-b729-812db8e9d5b6.png)

Then from the menu click on the "Build Now" or "Build with Parameters" to initiate the build
![image](https://user-images.githubusercontent.com/6670284/143384673-6bc8c9da-4dad-452c-acf2-ba07e2d9f13b.png)
Once a build is started, we can find the build link under "Build History" tag.

By clicking the running build from the "Build History" tag, we can go to the buid details page
and can monitor the build execution, access the build log, delete the build and also collect the OCS test report.
![image](https://user-images.githubusercontent.com/6670284/143462053-1c1a866c-3aa8-4a84-950d-5d02eae851c9.png)

OCS Test Report
Once we click the OCS test report link we can
find the zip file to download which will contains all the reports and the test run videos.
![image](https://user-images.githubusercontent.com/6670284/143462403-1649e35a-ee45-4404-a63f-ed6fbdbc1ac0.png)
![image](https://user-images.githubusercontent.com/6670284/143462495-3c1945b1-ca37-4d1f-bbaa-63def54c0db0.png)


