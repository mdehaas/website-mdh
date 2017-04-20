+++
date = "2016-06-01T22:04:17+02:00"
math = false
tags = ["powershell","dfs"]
title = "What's up with Grant-DfsnAccess?"
image = ""
teaser = "Grant-DfsnAccess has been a thorn in my eye for over a year now. It is in most cases an unusable Powershell cmdlet. Why? Because it does not do the most important job it should. It is not able switch a DFS link to use explicit permissions."
aliases = ["/post/2016/june/01/whats-up-with-grant-dfsnaccess/"]
+++

For our environment we use a selfservice portal (built in-house) where we are trying to seperate the actual code for performing an action from the front-end code. For our DFS infrastructure the most suitable solution is a PowerShell endpoint with purpose built functions. On of these is setting security groups on DFS links to allow Access Based Enumeration (ABE) to only show links the user actually has access to. For this I need to do a very ugly 'breakout' from Powershell and use the DfsUtil.exe.

```powershell
$Procs = Get-Process | Where {$_.Name -notlike "notepad*"}
```

The issue is however not completely isolated to Powershell since our old method -C&#35; code- was producing the same results. So the deeper problem in my opinion lies within the .NET Framework.

Still it is a shame this has been known for a long time and Microsoft doesn't seem to be working on a solution. I will be checking Windows Server 2016 TP5 shortly to find if this has been fixed

Please refer to [The Windows PowerShell cmdlet Grant-DfsnAccess does not change inheritance on DFS links](https://support.microsoft.com/en-us/kb/2938148) for the Microsft Knowledge Base article.