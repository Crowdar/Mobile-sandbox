Provides a testing environment integrating components needed to mobile devices testing executions

##Mobile sandbox components:
- seleniumGrid
- appium server
- android emulator
- no-vnc
- video recorder

##Requirements:
- linux
- git client   
     https://www.atlassian.com/git/tutorials/install-git
- docker 18.09    
     https://docs.docker.com/install/linux/docker-ce/ubuntu/
- docker compose 1.24   
     https://docs.docker.com/compose/install/

##Steps to start the sandbox:
- Open Terminal
- Execute git clone https://bitbucket.org/crowdarautomation/mobile-docker-framework.git
- Inside clone location execute "sudo apkDirectory=[YOUR_LOCAL_APK_DIRECTORY] docker-compose up" or "sudo apkDirectory=[YOUR_LOCAL_APK_DIRECTORY] docker-compose up -d" (daemon mode)
    - note: [YOUR_LOCAL_APK_DIRECTORY]: refers to the shared volume to be accessed by the container.   
        for example:      
                    sudo apkDirectory=./example/sample_apk docker-compose up (relative location)   
                    sudo apkDirectory=/home/apk docker-compose up  (absolute location)   
                      
---------------------------------------------------------------------------------------

## Steps to consume the sandbox

#### Now you need to configure your capabilities as follow

#### 		to be executed directly with appium server (http://127.0.0.1:4723/wd/hub)
        	DesiredCapabilities capabilities = DesiredCapabilities.android();
        	capabilities.setCapability("deviceName", "samsung_galaxy_s7_9.0");
            capabilities.setCapability(MobileCapabilityType.APP, "/root/tmp/sample_apk/sample_apk_debug.apk");   
               note: /root/tmp/sample_apk/ .... refers to to the container shared volume location previously defined.
                     in your case need to be setted as follow /root/tmp/sample_apk/[YOUR_APK_FILE].apk
        	
#### 		to be executed with selenium grid (http://127.0.0.1:4444/wd/hub
        	DesiredCapabilities capabilities = new DesiredCapabilities();
        	capabilities.setCapability("deviceName","Android Emulator");
        	capabilities.setCapability("automationName","automationName");
            capabilities.setCapability("browserName","android");
        	capabilities.setCapability("app", "/root/tmp/sample_apk/sample_apk_debug.apk");   
     	         note: /root/tmp/sample_apk/ .... refers to to the container shared volume location previously defined.
                     in your case need to be setted as follow /root/tmp/sample_apk/[YOUR_APK_FILE].apk
			
			#### You need what the emulator will be to use. Here two examples
        	capabilities.setCapability("avd","samsung_galaxy_s7_9.0");
            capabilities.setCapability("avd","nexus_5_7.1.1");
            
            
        	
            
---------------------------------------------------------------------------------------
#### To connect via no-vnc see docker-compose file to view port forwaded to 6080 and open http://localhost:6080 from web browser

##Troubleshooting
docker exec -it [CONTAINER-NAME] tail -f /var/log/supervisor/docker-android.stdout.log

##enjoy!

for more information: https://github.com/budtmo/docker-android

