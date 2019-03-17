# Lab 3: Creating a Dashboard using API

In this lab, we will create a dashsboard using the Dashboard API.

## Step-by-step Guide - Access API Explorer

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API > Dynatrace API Explorer**

Select Environment API from the top right drop down menu.

## Step-by-step Guide - Create Dashboard using API

1. In the API list select **Dashboards** 

2. Select **POST /dashboards**

![Dashboard API](/assets/dashboard-config-post.png)

3. Select **Try it Out**

4. The following json will create a dashboard. Copy the JSON into the Example Value field

```json
{
  "metadata": {
    "clusterVersion": "1.162.140.20190225-132002",
    "configurationVersions": [
      2
    ]
  },
  "id": "cd3dbb72-bd6b-4d3a-966b-ca07741b669b",
  "dashboardMetadata": {
    "name": "Executive Overview",
    "owner": "admin",
    "timeframe": "l_2_HOURS",
    "managementZone": null
  },
  "tiles": [
    {
      "name": "Top web applications",
      "tileType": "APPLICATIONS_MOST_ACTIVE",
      "configured": true,
      "bounds": {
        "top": 494,
        "left": 0,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null
    },
    {
      "name": "Overview",
      "tileType": "HEADER",
      "configured": true,
      "bounds": {
        "top": 0,
        "left": 0,
        "width": 304,
        "height": 38
      },
      "useComparisionTimeframe": false,
      "managementZone": null
    },
    {
      "name": "Problems",
      "tileType": "OPEN_PROBLEMS",
      "configured": true,
      "bounds": {
        "top": 38,
        "left": 0,
        "width": 152,
        "height": 152
      },
      "useComparisionTimeframe": false,
      "managementZone": null
    },
    {
      "name": "Service health",
      "tileType": "SERVICES",
      "configured": true,
      "bounds": {
        "top": 798,
        "left": 152,
        "width": 152,
        "height": 152
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "filterConfig": null,
      "chartVisible": true
    },
    {
      "name": "Host health",
      "tileType": "HOSTS",
      "configured": true,
      "bounds": {
        "top": 798,
        "left": 0,
        "width": 152,
        "height": 152
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "filterConfig": null,
      "chartVisible": true
    },
    {
      "name": "Application health",
      "tileType": "APPLICATIONS",
      "configured": true,
      "bounds": {
        "top": 38,
        "left": 152,
        "width": 152,
        "height": 152
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "filterConfig": null,
      "chartVisible": true
    },
    {
      "name": "World map",
      "tileType": "APPLICATION_WORLDMAP",
      "configured": true,
      "bounds": {
        "top": 38,
        "left": 380,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ],
      "metric": "APDEX"
    },
    {
      "name": "Synthetic monitor health",
      "tileType": "SYNTHETIC_TESTS",
      "configured": true,
      "bounds": {
        "top": 76,
        "left": 1292,
        "width": 304,
        "height": 266
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "filterConfig": null,
      "chartVisible": true
    },
    {
      "name": "easyTravel Production Overview",
      "tileType": "HEADER",
      "configured": true,
      "bounds": {
        "top": 0,
        "left": 380,
        "width": 912,
        "height": 38
      },
      "useComparisionTimeframe": false,
      "managementZone": null
    },
    {
      "name": "User behavior",
      "tileType": "SESSION_METRICS",
      "configured": true,
      "bounds": {
        "top": 342,
        "left": 380,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ]
    },
    {
      "name": "User breakdown",
      "tileType": "USERS",
      "configured": true,
      "bounds": {
        "top": 342,
        "left": 684,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ]
    },
    {
      "name": "Bounce rate",
      "tileType": "BOUNCE_RATE",
      "configured": true,
      "bounds": {
        "top": 342,
        "left": 988,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ]
    },
    {
      "name": "JavaScript errors",
      "tileType": "UEM_JSERRORS_OVERALL",
      "configured": true,
      "bounds": {
        "top": 646,
        "left": 380,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ]
    },
    {
      "name": "Resources",
      "tileType": "RESOURCES",
      "configured": true,
      "bounds": {
        "top": 646,
        "left": 988,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ],
      "metric": "ACTION_COUNT"
    },
    {
      "name": "Most used 3rd parties",
      "tileType": "THIRD_PARTY_MOST_ACTIVE",
      "configured": true,
      "bounds": {
        "top": 646,
        "left": 684,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ],
      "metric": "ACTION_COUNT"
    },
    {
      "name": "Live user activity",
      "tileType": "UEM_ACTIVE_SESSIONS",
      "configured": true,
      "bounds": {
        "top": 190,
        "left": 0,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null
    },
    {
      "name": "Web application",
      "tileType": "APPLICATION",
      "configured": true,
      "bounds": {
        "top": 38,
        "left": 988,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ]
    },
    {
      "name": "Browser monitor",
      "tileType": "SYNTHETIC_SINGLE_WEBCHECK",
      "configured": true,
      "bounds": {
        "top": 342,
        "left": 1292,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "SYNTHETIC_TEST-7C8DA81C3D924F91"
      ],
      "excludeMaintenanceWindows": false
    },
    {
      "name": "Browser monitor",
      "tileType": "SYNTHETIC_SINGLE_WEBCHECK",
      "configured": true,
      "bounds": {
        "top": 646,
        "left": 1292,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "SYNTHETIC_TEST-7B366FE3C49E44B0"
      ],
      "excludeMaintenanceWindows": false
    },
    {
      "name": "World map",
      "tileType": "APPLICATION_WORLDMAP",
      "configured": true,
      "bounds": {
        "top": 38,
        "left": 684,
        "width": 304,
        "height": 304
      },
      "useComparisionTimeframe": false,
      "managementZone": null,
      "assignedEntities": [
        "APPLICATION-B015199D5B489C02"
      ],
      "metric": "SESSION_USERS"
    },
    {
      "name": "Active Monitoring",
      "tileType": "HEADER",
      "configured": true,
      "bounds": {
        "top": 38,
        "left": 1292,
        "width": 304,
        "height": 38
      },
      "useComparisionTimeframe": false,
      "managementZone": null
    },
    {
      "name": "easyTravel Production",
      "tileType": "HEADER",
      "configured": true,
      "bounds": {
        "top": 0,
        "left": 1292,
        "width": 304,
        "height": 38
      },
      "useComparisionTimeframe": false,
      "managementZone": null
    }
  ]
}
```

5. Select **Execute**, to create your browser test.

If you used the same names used throughout these labs then the above dashboard should display correctly. If you used other names, then you will need to change the ids used in the above JSON. The ids used in the above JSON are:

**Application Id**

Find: APPLICATION-B015199D5B489C02

Replace: with your application id of “easyTravel Production”

**Basic Browser Test**

Find: SYNTHETIC_TEST-7C8DA81C3D924F91

Replace: with your synthetic id of your “easyTravel Homepage Browser Check”

**Multi Step Browser Test**

Find: SYNTHETIC_TEST-7B366FE3C49E44B0

Replace: with your synthetic id of your “easyTravel Multi Step Browser Check”


:arrow_up: [Back to TOC](/README.md)
