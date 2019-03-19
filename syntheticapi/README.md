# Lab 2: Creating Synthetic Transactions using API

In this lab, we will create a 2 synthetic transactions - a basic browser test and a multi-step transaction. 


## Step-by-step Guide - Access API Explorer

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API > Dynatrace API Explorer**

Select **Environment API** from the top right drop down menu.


## Step-by-step Guide - Create a Simple Synthetic Browser Test

1. In the API list select **Synthetic** 

2. Select **POST /synthetic/monitors**

![Synthetic API](/assets/synthetic-config-post.png)

3. Select **Try it Out**

4. The following json will create a browser test against the easyTravel homepage from Sydney and Singapore.

However, you need to change the script to "point" to the external ip address of your easyTravel Production server.

Copy the following JSON into a txt editor.

Modify the JSON (find/replace), the existing IP address (13.210.14.153) to the IP address if your external production server. 

You will find the IP address in 2 locations.

Only the IP addresses need changing, no further changes are required.

Copy the resulting JSON into the Example Value field

**Single Browser Test JSON***

```json
{
  "name": "easyTravel Production - Homepage",
  "frequencyMin": 5,
  "enabled": true,
  "type": "BROWSER",
  "script": "{\r\n    \"configuration\": {\r\n        \"device\": {\r\n            \"orientation\": \"landscape\",\r\n            \"deviceName\": \"Desktop\"\r\n        }\r\n    },\r\n    \"type\": \"availability\",\r\n    \"version\": \"1.0\",\r\n    \"events\": [{\r\n        \"type\": \"navigate\",\r\n        \"wait\": {\r\n            \"waitFor\": \"page_complete\"\r\n        },\r\n        \"description\": \"Loading of \\\"http:\/\/13.210.14.153:8079\/\\\"\",\r\n        \"url\": \"http:\/\/13.210.14.153:8079\/\"\r\n    }]\r\n}",
  "locations": [
    "GEOLOCATION-191EF52906549983",
    "GEOLOCATION-635E708B828A7881",
    "GEOLOCATION-2FD31C834DE4D601"
  ],
  "anomalyDetection": {
    "outageHandling": {
      "globalOutage": true,
      "localOutage": false,
      "localOutagePolicy": {
        "affectedLocations": 1,
        "consecutiveRuns": 3
      }
    },
    "loadingTimeThresholds": {
      "enabled": false,
      "thresholds": []
    }
  },
  "tags": [],
  "managementZones": []
}
```

5. Select **Execute**, to create your browser test.

Save the returned Synthetic Id as you may need it later!

## Step-by-step Guide - Create a Multi-Step Synthetic Browser Test

6. The following json will create a multi step browser against your easyTravel production environment from Sydney and Singapore.

Find / Replace **13.210.14.153** with the IP address if your external production server.

You will find the IP address in 2 locations.

Copy the resulting JSON into the Example Value field

```json
{
  "name": "easyTravel Production - Multi Step",
  "frequencyMin": 5,
  "enabled": true,
  "type": "BROWSER",
  "script": "{\r\n    \"configuration\": {\r\n        \"device\": {\r\n            \"orientation\": \"landscape\",\r\n            \"deviceName\": \"Desktop\"\r\n        }\r\n    },\r\n    \"type\": \"clickpath\",\r\n    \"version\": \"1.0\",\r\n    \"events\": [{\r\n        \"type\": \"navigate\",\r\n        \"wait\": {\r\n            \"waitFor\": \"page_complete\"\r\n        },\r\n        \"description\": \"Loading of \\\"http:\/\/13.210.14.153:8079\/\\\"\",\r\n        \"url\": \"http:\/\/13.210.14.153:8079\/\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"network\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm\\\\:loginLink\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"a:contains(\\\"Login\\\")\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"div:contains(\\\"Login\\\"):eq(4)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".iceCmdLnk:eq(0)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm div:nth-child(6) a\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"loginForm:loginLink\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"network\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm\\\\:j_idt58\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"input[type=\\\"image\\\"][src$=\\\"img\/privacypolicy_lock.png\\\"][name=\\\"loginForm:j_idt58\\\"]\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".iceCmdBtn:eq(0)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm\\\\:j_idt51 input:nth-child(7)\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"loginForm:j_idt58\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"network\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm\\\\:j_idt63\\\\:2\\\\:j_idt64\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"a:contains(\\\"clarettatak\\\"):eq(1)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"div:contains(\\\"bonaventurahar\\\"):eq(7)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".iceCmdLnk:eq(23)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm\\\\:j_idt63 a:nth-child(5)\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"loginForm:j_idt63:2:j_idt64\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"page_complete\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"a:contains(\\\"Book Now\\\"):eq(1)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"div:contains(\\\"If you wish to stay in a hotel that has friendly staff and an inviting ambience that reminds you of home, then head to the Grand Hotel.\\\"):eq(4)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".commonButton:eq(5)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#recommendation div div:nth-child(2) div:nth-child(2) a:nth-child(5)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#recommendation div.icePnlPos div.icePnlGrp div.icePnlGrp a.commonButton:eq(0)\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"Book Now\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"page_complete\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform\\\\:bookReviewNext\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"a:contains(\\\"Next\\\")\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"div:contains(\\\"To look for a different journey please press the\\\"):eq(4)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".commonButton:eq(5)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform div:nth-child(6) a:nth-child(7)\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"iceform:bookReviewNext\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"network\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform\\\\:j_idt118\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"input[type=\\\"image\\\"][src$=\\\"img\/privacypolicy_lock.png\\\"][name=\\\"iceform:j_idt118\\\"]\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".iceCmdBtn:eq(3)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform div:nth-child(6) div:nth-child(5) input\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"iceform:j_idt118\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"page_complete\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform\\\\:bookPaymentNext\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"input[type=\\\"submit\\\"][name=\\\"iceform:bookPaymentNext\\\"]\"\r\n            }, {\r\n                \"type\": \"dom\",\r\n                \"value\": \"document.forms[1][10]\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".iceCmdBtn:eq(4)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform div:nth-child(6) input:nth-child(7)\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"Next\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"page_complete\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform\\\\:bookFinishFinish\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"input[type=\\\"submit\\\"][name=\\\"iceform:bookFinishFinish\\\"]\"\r\n            }, {\r\n                \"type\": \"dom\",\r\n                \"value\": \"document.forms[1][4]\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".iceCmdBtn:eq(3)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#iceform div:nth-child(6) input:nth-child(6)\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"Finish\\\"\"\r\n    }, {\r\n        \"type\": \"click\",\r\n        \"wait\": {\r\n            \"waitFor\": \"page_complete\"\r\n        },\r\n        \"target\": {\r\n            \"locators\": [{\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm\\\\:logoutLink\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"a:contains(\\\"Gold status!\\n\\t\\tLogout\\\")\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"div:contains(\\\"Gold status!\\\"):eq(4)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \".iceOutLnk:eq(1)\"\r\n            }, {\r\n                \"type\": \"css\",\r\n                \"value\": \"#loginForm div:nth-child(7) a\"\r\n            }]\r\n        },\r\n        \"button\": 0,\r\n        \"description\": \"click on \\\"loginForm:logoutLink\\\"\"\r\n    }]\r\n}\r\n",
  "locations": [
    "GEOLOCATION-191EF52906549983",
    "GEOLOCATION-635E708B828A7881",
    "GEOLOCATION-2FD31C834DE4D601"
  ],
  "anomalyDetection": {
    "outageHandling": {
      "globalOutage": true,
      "localOutage": false,
      "localOutagePolicy": {
        "affectedLocations": 1,
        "consecutiveRuns": 3
      }
    },
    "loadingTimeThresholds": {
      "enabled": false,
      "thresholds": []
    }
  },
  "tags": [],
  "managementZones": []
}
```

5. Select **Execute**, to create your multi step browser test. 

Save the returned Synthetic Id as you may need it later!

:arrow_up: [Back to TOC](/README.md)
