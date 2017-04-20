+++
date = "2016-10-10T21:54:51+02:00"
draft = false
image = ""
math = false
tags = []
teaser = "Having trouble connecting multiple OMS workspaces when the connection is made using the OMS Gateway Service Preview? The errorcode you see in the Micorosoft Management Agent is 12019. The same error is in the eventlog of the OMS Gateway server."
title = "Connecting workspaces through OMS Gateway"

+++

This took some time to figure this out becasue I was a little impatient between tests. It seems that the OMS gateway needs to be in all the workspaces that you want to connect through it. I haven't seen this documented anywhere yet, other than you need a working connection to the OMS cloud. It makes sense though because the client uses certificates to communicate to the Azure backend. Apparently the OMS Gateway service is not able to perform this action, most likely because it does not know the keys for the workspace.

At first I also thought that you needed to restart the OMS Gateway service to allow the OMS Gayeway to connect. In my final testing I just waited and only reloaded the config of the agent. This also results in a working connection. So please be more patient than I was.

Just to be clear. The OMS Gateway eventlog wil have the following error:
```
Log Name:      OMS Gateway Log
Source:        OMS Gateway
Date:          10-10-2016 11:26:22
Event ID:      105
Task Category: None
Level:         Error

Description:
2016-10-10 11:26:22 [12] ERROR GatewayLogic - Target host (<WORKSPACE ID>.oms.opinsights.azure.com) is forbidden.
```

The Microsoft Monitoring Agent (MMA) controlpanel applet will show the following error (also seen when using Powershell to manage the MMA):

> The agent had an unknown failure 12019.  The Operations Manager event log may have more information. If the error continues, please contact support.

I hope this helps others getting OMS Gateway working with multiple workspaces.