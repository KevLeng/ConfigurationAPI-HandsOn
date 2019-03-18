# Lab 2: Creating a Applications using the Application API's

In this lab, we will create a 4 applications using the swagerised application configuration API.

## Step-by-step Guide - Access API Explorer

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API > Dynatrace API Explorer**

Select Configuration API from the top right drop down menu.

## Step-by-step Guide - Create the Application

1. In the API list select **Web Application configuration**

2. Select **POST /applications/web**

![Creates a new web application](/assets/web-application-config-post.png)

3. Select **Try it Out**

4. Copy the following application configuration JSON into the Example Value field

**Application Configuration JSON**

```json
{
  "name": "easyTravel Production (by API)",
  "realUserMonitoringEnabled": true,
  "costControlUserSessionPercentage": 100,
  "loadActionKeyPerformanceMetric": "ACTION_DURATION",
  "xhrActionKeyPerformanceMetric": "ACTION_DURATION",
  "loadActionApdexSettings": {
    "threshold": 3,
    "considerJavaScriptErrors": true
  },
  "xhrActionApdexSettings": {
    "threshold": 2.5,
    "considerJavaScriptErrors": false
  },
  "customActionApdexSettings": {
    "threshold": 3,
    "considerJavaScriptErrors": true
  },
  "waterfallSettings": {
    "uncompressedResourcesThreshold": 860,
    "resourcesThreshold": 100000,
    "resourceBrowserCachingThreshold": 50,
    "slowFirstPartyResourcesThreshold": 200000,
    "slowThirdPartyResourcesThreshold": 200000,
    "slowCdnResourcesThreshold": 200000
  },
  "monitoringSettings": {
    "fetchRequests": false,
    "xmlHttpRequest": true,
    "javaScriptFrameworkSupport": {
      "angular": false,
      "dojo": false,
      "extJS": false,
      "icefaces": true,
      "jQuery": true,
      "mooTools": false,
      "prototype": true,
      "activeXObject": false
    },
    "contentCapture": {
      "resourceTimingSettings": {
        "w3cResourceTimings": true,
        "nonW3cResourceTimings": false,
        "nonW3cResourceTimingsInstrumentationDelay": 50,
        "resourceTimingCaptureType": "CAPTURE_FULL_DETAILS",
        "resourceTimingsDomainLimit": 10
      },
      "javaScriptErrors": true,
      "timeoutSettings": {
        "timedActionSupport": false,
        "temporaryActionLimit": 0,
        "temporaryActionTotalTimeout": 100
      },
      "visuallyCompleteAndSpeedIndex": true
    },
    "excludeXhrRegex": "",
    "injectionMode": "JAVASCRIPT_TAG",
    "libraryFileLocation": "",
    "monitoringDataPath": "",
    "customConfigurationProperties": "",
    "serverRequestPathId": "",
    "secureCookieAttribute": false,
    "cookiePlacementDomain": "",
    "cacheControlHeaderOptimizations": true,
    "advancedJavaScriptTagSettings": {
      "syncBeaconFirefox": false,
      "syncBeaconInternetExplorer": false,
      "instrumentUnsupportedAjaxFrameworks": false,
      "specialCharactersToEscape": "",
      "maxActionNameLength": 100,
      "maxErrorsToCapture": 10,
      "additionalEventHandlers": {
        "userMouseupEventForClicks": false,
        "clickEventHandler": false,
        "mouseupEventHandler": false,
        "blurEventHandler": false,
        "changeEventHandler": false,
        "toStringMethod": false,
        "maxDomNodesToInstrument": 5000
      },
      "eventWrapperSettings": {
        "click": false,
        "mouseUp": false,
        "change": false,
        "blur": false,
        "touchStart": false,
        "touchEnd": false
      },
      "globalEventCaptureSettings": {
        "mouseUp": true,
        "mouseDown": true,
        "click": true,
        "doubleClick": true,
        "keyUp": true,
        "keyDown": true,
        "scroll": true,
        "additionalEventCapturedAsUserInput": ""
      }
    }
  }
}
```

Paste above JSON into Example Value field

![Web application configuration example value](/assets/web-application-config-examplevalue.png)

5. Select **Execute**, record the returned application id as you will need it later in this lab.

![Web application configuration success](/assets/web-application-config-success.png)

Success, production application has been created.

6.  Now lets create the application for staging: Modify the application name. In the Example Value field, change the **name** to **easyTravel Staging (by API)**

```json
  "name": "easyTravel Staging (by API)",
```

Execute again and record the application id's returned.

Success, staging application has been created.

7. Now lets create the B2B applications, use the following JSON. Copy/paste into the example value field and select **execute**

Remember to record the returned application id.

```json
{
  "name": "easyTravel B2B Production (by API)",
  "realUserMonitoringEnabled": true,
  "costControlUserSessionPercentage": 100,
  "loadActionKeyPerformanceMetric": "ACTION_DURATION",
  "xhrActionKeyPerformanceMetric": "ACTION_DURATION",
  "loadActionApdexSettings": {
    "threshold": 3,
    "considerJavaScriptErrors": true
  },
  "xhrActionApdexSettings": {
    "threshold": 2.5,
    "considerJavaScriptErrors": false
  },
  "customActionApdexSettings": {
    "threshold": 3,
    "considerJavaScriptErrors": true
  },
  "waterfallSettings": {
    "uncompressedResourcesThreshold": 860,
    "resourcesThreshold": 100000,
    "resourceBrowserCachingThreshold": 50,
    "slowFirstPartyResourcesThreshold": 200000,
    "slowThirdPartyResourcesThreshold": 200000,
    "slowCdnResourcesThreshold": 200000
  },
  "monitoringSettings": {
    "fetchRequests": false,
    "xmlHttpRequest": false,
    "javaScriptFrameworkSupport": {
      "angular": false,
      "dojo": false,
      "extJS": false,
      "icefaces": false,
      "jQuery": false,
      "mooTools": false,
      "prototype": false,
      "activeXObject": false
    },
    "contentCapture": {
      "resourceTimingSettings": {
        "w3cResourceTimings": true,
        "nonW3cResourceTimings": false,
        "nonW3cResourceTimingsInstrumentationDelay": 50,
        "resourceTimingCaptureType": "CAPTURE_FULL_DETAILS",
        "resourceTimingsDomainLimit": 10
      },
      "javaScriptErrors": true,
      "timeoutSettings": {
        "timedActionSupport": false,
        "temporaryActionLimit": 0,
        "temporaryActionTotalTimeout": 100
      },
      "visuallyCompleteAndSpeedIndex": true
    },
    "excludeXhrRegex": "",
    "injectionMode": "JAVASCRIPT_TAG",
    "libraryFileLocation": "",
    "monitoringDataPath": "",
    "customConfigurationProperties": "",
    "serverRequestPathId": "",
    "secureCookieAttribute": false,
    "cookiePlacementDomain": "",
    "cacheControlHeaderOptimizations": true,
    "advancedJavaScriptTagSettings": {
      "syncBeaconFirefox": false,
      "syncBeaconInternetExplorer": false,
      "instrumentUnsupportedAjaxFrameworks": false,
      "specialCharactersToEscape": "",
      "maxActionNameLength": 100,
      "maxErrorsToCapture": 10,
      "additionalEventHandlers": {
        "userMouseupEventForClicks": false,
        "clickEventHandler": false,
        "mouseupEventHandler": false,
        "blurEventHandler": false,
        "changeEventHandler": false,
        "toStringMethod": false,
        "maxDomNodesToInstrument": 5000
      },
      "eventWrapperSettings": {
        "click": false,
        "mouseUp": false,
        "change": false,
        "blur": false,
        "touchStart": false,
        "touchEnd": false
      },
      "globalEventCaptureSettings": {
        "mouseUp": true,
        "mouseDown": true,
        "click": true,
        "doubleClick": true,
        "keyUp": true,
        "keyDown": true,
        "scroll": true,
        "additionalEventCapturedAsUserInput": ""
      }
    }
  }
}
```
 Remember to record the returned application id.

8. Last one: In the Example Value field, change the **name** to **easyTravel B2B Staging (by API)**

```json
  "name": "easyTravel B2B Staging (by API)",
```

Execute again and record the application id returned.

9. Now you should have 4 applications, check in Dynatrace to confirm

![Web applications complete](/assets/web-applications-complete.png)


## Step-by-step Guide - Create the Application Detection Rules

Now we need to create the application detection rules.

1. Select **Web Application detection configuration**

2. Select **POST /applicationdetectionRules**

![Creates a application detection rule](/assets/web-application-detection-config-post.png)

3. Select **Try it Out**

4. Copy the following application detection JSON into the Example Value field

Replace **YOUR-Application-ID** with your **application id** (you recorded earlier) for **easyTravel Production (by API)**

Replace **YOUR-IPAddress** with the **internal ip address** for your **Production** server

```json
{
  "applicationIdentifier": "YOUR-Application-ID",
  "filterConfig": {
    "pattern": "YOUR-IPAddress:8079",
    "applicationMatchType": "CONTAINS",
    "applicationMatchTarget": "URL"
  }
}
```

The following image is an example only:

![Application detection rule example](/assets/detectionrule-example.PNG)

Select **Execute***

Now replace the internal IP address with your external IP address.

Select **Execute***

Success, rules for the **easyTravel Production (by API)** are done. View them in the Dynatrace UI.

5. Now lets create the detection rules for easyTravel **Staging** (by API) application. Repeat the above step using the application id and internal / external ip addresses for **easyTravel Staging (by API)**

Once you have submitted the rules, lets move on to the the easyTravel B2B applications. 

6. Use the following JSON to create the detection rules for your easyTravel B2B Production (by API) and easyTravel B2B Staging (by API) applications.

Remember to use your production / staging ip addresses.

```json
{
  "applicationIdentifier": "YOUR-Application-ID",
  "filterConfig": {
    "pattern": "YOUR-IPAddress:8999",
    "applicationMatchType": "CONTAINS",
    "applicationMatchTarget": "URL"
  }
}
```
:arrow_up: [Back to TOC](/README.md)
