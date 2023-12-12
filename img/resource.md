fetch logs, from:now()-24h
| makeTimeseries count = count(), by:{Content, "location : eastus"}, time:{timestamp}


fetch logs, from:now()-24h
| makeTimeseries count = count(), by:{Content, "RoleLocation : East US 2"}, time:{timestamp}



| filter matchesValue(cloud.region, "eastus")

| filter matchesValue(cloud.region, "eastus") and matchesValue(cloud.provider, "Azure")

| filter matchesValue(event.type, "LOG")

| filter matchesValue(azure.resource.group, "RESOURCE") and matchesValue(azure.resource.type, "MICROSOFT.STORAGE/STORAGEACCOUNTS")

fetch logs //, scanLimitGBytes: 500, samplingRatio: 1000
| filter matchesValue(azure.resource.group, "RESOURCE") and matchesValue(azure.resource.id, "/SUBSCRIPTIONS/69349ACF-2A6C-409D-A925-96BA0C5F099F/RESOURCEGROUPS/RESOURCE/PROVIDERS/MICROSOFT.WEB/SITES/FUNCTIONDYNATRACE-FUNCTION")
| sort timestamp desc
