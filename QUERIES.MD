# Azure PaaS elasticity load testing Queries

These were the queries used to gather the data from Azure Monitor.

<table style="width:100%">
  <tr>
    <th>Test id</th>
    <th>Function App Instance Query</th>
    <th>Function App RPS Query</th>
    <th>EventHub Incoming Messages Query</th>
  </tr>
  <tr>
    <td>15/04/2021 13:15:43 (K)</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>15/04/2021 12:45:44 (K)</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>16/04/2021-17:15:13-(V)</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>23/04/2021 07:57:57</td>
    <td>
let min_t = datetime(2021-04-23 05:56:00Z);<br>
let max_t = datetime(2021-04-23 06:13:00Z);<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize Count_Function_App_Instances=dcount(cloud_RoleInstance) by bin(timestamp, 30s)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 05:56:00Z);<br>
let max_t = datetime(2021-04-23 06:13:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize ['rate/second'] = sum(itemCount) / grainPerSecond by bin(timestamp, grainTime)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 05:56:00Z);<br>
let max_t = datetime(2021-04-23 06:13:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
AzureMetrics<br>
| where TimeGenerated between(min_t..max_t)<br>
| where Resource == "FUNCEHTEHNS" and MetricName == "IncomingMessages"<br>
| summarize ['Total Messages'] = sum(Total)<br>
    </td>
  </tr>
  <tr>
    <td>23/04/2021 08:34:33</td>
    <td>
let min_t = datetime(2021-04-23 06:35:00Z);<br>
let max_t = datetime(2021-04-23 06:50:00Z);<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize Count_Function_App_Instances=dcount(cloud_RoleInstance) by bin(timestamp, 30s)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 06:35:00Z);<br>
let max_t = datetime(2021-04-23 06:50:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize ['rate/second'] = sum(itemCount) / grainPerSecond by bin(timestamp, grainTime)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 06:35:00Z);<br>
let max_t = datetime(2021-04-23 06:50:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
AzureMetrics<br>
| where TimeGenerated between(min_t..max_t)<br>
| where Resource == "FUNCEHTEHNS" and MetricName == "IncomingMessages"<br>
| summarize ['Total Messages'] = sum(Total)<br>
    </td>
  </tr>
  <tr>
    <td>23/04/2021 09:54:49</td>
    <td>
let min_t = datetime(2021-04-23 07:59:00Z);<br>
let max_t = datetime(2021-04-23 08:14:00Z);<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize Count_Function_App_Instances=dcount(cloud_RoleInstance) by bin(timestamp, 30s)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 07:59:00Z);<br>
let max_t = datetime(2021-04-23 08:14:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize ['rate/second'] = sum(itemCount) / grainPerSecond by bin(timestamp, grainTime)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 07:59:00Z);<br>
let max_t = datetime(2021-04-23 08:14:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
AzureMetrics<br>
| where TimeGenerated between(min_t..max_t)<br>
| where Resource == "FUNCEHTEHNS" and MetricName == "IncomingMessages"<br>
| summarize ['Total Messages'] = sum(Total)<br>
    </td>
  </tr>
  <tr>
    <td>23/04/2021 10:34:32</td>
    <td>
let min_t = datetime(2021-04-23 08:45:00Z);<br>
let max_t = datetime(2021-04-23 09:00:00Z);<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize Count_Function_App_Instances=dcount(cloud_RoleInstance) by bin(timestamp, 30s)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 08:45:00Z);<br>
let max_t = datetime(2021-04-23 09:00:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
requests<br>
| where timestamp between(min_t..max_t)<br>
| summarize ['rate/second'] = sum(itemCount) / grainPerSecond by bin(timestamp, grainTime)<br>
| render timechart<br>
    </td>
    <td>
let min_t = datetime(2021-04-23 08:45:00Z);<br>
let max_t = datetime(2021-04-23 09:00:00Z);<br>
let grainTime = 1min;<br>
let grainPerSecond = 1.0 * 60.0; // Rate per second<br>
AzureMetrics<br>
| where TimeGenerated between(min_t..max_t)<br>
| where Resource == "FUNCEHTEHNS" and MetricName == "IncomingMessages"<br>
| summarize ['Total Messages'] = sum(Total)<br>
    </td>
  </tr>
</table>
