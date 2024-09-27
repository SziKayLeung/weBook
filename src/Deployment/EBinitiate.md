## Initiate the Elastic Beanstalk application

1. Connect to AWS through command prompt by copying the AWS window access paths.
    ```
    SET AWS_ACCESS_KEY_ID=<aws_access_key_id>
    SET AWS_SECRET_ACCESS_KEY=<aws_secret_access_key>
    SET AWS_SESSION_TOKEN=<aws_session_token>
    ```
    > **Note:** The AWS access keys update every now and then, so need to copy the access keys frequently and paste into the Windows command prompt.

    - Use the administrative access if possible.
    ![AwsAccess](../Images/AwsAccess.jpg)

    - Copy the keys from the Windows tab, under Option 1. 
    ![AwsAccess2](../Images/AwsAccess2.jpg)

2. Set up the eb platform. 
    ```shell
    eb platform select 

    Select a platform.
    1) .NET Core on Linux
    2) .NET on Windows Server
    3) Docker
    4) Go
    5) Java
    6) Node.js
    7) PHP
    8) Packer
    9) Python
    10) Ruby
    11) Tomcat
    (make a selection): 9 # Python

    Select a platform branch.
    1) Python 3.11 running on 64bit Amazon Linux 2023
    2) Python 3.9 running on 64bit Amazon Linux 2023
    3) Python 3.8 running on 64bit Amazon Linux 2
    4) Python 3.7 running on 64bit Amazon Linux 2 (Deprecated)
    (default is 1): 1
    ```

3. Initiate the Elastic Beanstalk application, which creates a config.yml.
    ```shell
    eb init -p python-3.11 isoVisDev
    ```
    > **Note:** Ensure that the region is correct (matching with region stated in the AWS web) in the config.yml

    The config.yml is created in the .elasticbeanstalk folder. 
    ``` 
     isoVisDev
     ├───manage.py
     ├───requirements.txt
     ├───.ebextensions
     |     ├───django.config
     ├───.elasticbeanstalk
     |     ├───config.yml  
     └───isoVisDev
    ```
    And the content of the config.yml:
    ```yaml
    branch-defaults:
      default:
        environment: isoVisDev
        group_suffix: null
      main:
        environment: isoVisDev
    global:
      application_name: isoVisDev
      branch: null
      default_ec2_keyname: null
      default_platform: Python 3.11
      default_region: eu-north-1        # change this region
      include_git_submodules: true
      instance_profile: null
      platform_name: null
      platform_version: null
      profile: null
      repository: null
      sc: null
      workspace_type: Application
    ```

4. Create Elastic Beanstalk environment to run application.
    ```shell
    eb create isoVisDev-env --region eu-north-1 
    eb status
    ```
    > **Note:** This creates the isoVisDev-env. Replace this with the name of environment to create. 
