# azure-function-log-analytics
Simple solution to send JSON logs from Azure Event Grid to Azure Log Analytics via Azure Function

# Description

This script automatically sends Azure Event Grid events to Azure Function.  
Azure Function then processes the json event and sends it to Azure Log Analytics

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## ✨ Features
- Sends JSON Events from Azure Event Grid to Azure Log Analytics
- Can be modified to be receive events from HTTPs/Webhooks, Event Queue, Event Grids, etc 

## 📦 Requirements
- Python 3.9+
- Azure Function
- Azure Log Analytics
- Github Actions

## 🚀 Setup

```bash
git clone https://github.com/roedinaranda/azure-function-log-analytics.git
cd azure-function-log-analytics
```

You can automate the deployment from GitHub to Azure Function by using GitHub Actions  
1. In .github/workflows/azure-functions-app-python.yml modify the variables below  
`AZURE_FUNCTIONAPP_NAME`  
2. In Settings ->  Security -> Secrets and Variables -> Actions create a `AZURE_FUNCTIONAPP_PUBLISH_PROFILE`
3. Go to your Azure Function App -> Overview -> Get publish profile. This will download a file
4. Get the contents of the file and set it on your `AZURE_FUNCTIONAPP_PUBLISH_PROFILE` secret  

The json format you send in the function app will determine the column names that will be published on the log analytics table  
Refer to the sample below  

```json
[   
    {  
        'column1': 'data1',  
        'column2': 'data2',  
        'column3': 'data3'  
    },  
    {  
        'column1': 'data4',  
        'column2': 'data5',  
        'column3': 'data6'  
    }  
]
```
--- 

| column1 | column2 | column3 |
|------|------------|------|
| data1 | data2 | data3 |
| data4 | data5 | data6 |
