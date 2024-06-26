---
layout: post
title: Large PowerBI Dataset
---

Recently at work, I needed to change a PowerBI dataset to include all historical records. Previously, the Dashboard only included records associated with individuals who were active members in our database. A stakeholder requested that inactive members be included as well.  This increased the record count to over a million.  

Having such a large dataset made development difficult.  The load time of the records took over 30 minutes on my local computer.  I used this [Guy in a Cube video](https://www.youtube.com/watch?v=_zYvybVMk7k).  The video leads one through how to set a parameter that can be used to toggle a row limit.  This parameter can be used both locally, and on SharePoint. 

I was wary of having such a large dataset in an active dashboard.  I am sure that there are other ways to limit the data that may be more efficient.  However, the present solution works well, and I was able to deliver an update which met the stakeholders needs in a short turnaround time.  While the dashboard is in production, I can work on better optimized solutions.