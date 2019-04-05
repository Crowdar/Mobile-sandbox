# mobile-dkr-fwk
##Mobile sandbox:
- seleniumGrid
- appium server
- android emulator


##Requirements:
- linux


##Steps:
- Open Terminal
- Go to git clone location
- Execute "sudo docker-compose up" or "sudo docker-compose up -d" (daemon mode)

---------------------------------------------------------------------------------------
#### Now you need to configure your capabilities as follow

#### 		to be executed directly with appium server
        	DesiredCapabilities capabilities = DesiredCapabilities.android();
        	capabilities.setCapability("deviceName", "nexus_5_7.1.1");
            capabilities.setCapability(MobileCapabilityType.APP, "/root/tmp/sample_apk/FletNET_testing.apk");
        	
#### 		to be executed with selenium grid
        	DesiredCapabilities capabilities = new DesiredCapabilities();
        	capabilities.setCapability("deviceName","Android Emulator");
        	capabilities.setCapability("automationName","automationName");
        	capabilities.setCapability("app", "/root/tmp/sample_apk/FletNET_testing.apk");
        	capabilities.setCapability("browserName","android");
			
			#### You need what the emulator will be to use. Here two examples
        	capabilities.setCapability("avd","nexus_5_7.1.1");
        	capabilities.setCapability("avd","samsung_galaxy_s7_9.0");
            
##enjoy!


for more information: https://github.com/budtmo/docker-android

