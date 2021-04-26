# Azure PaaS elasticity load testing

This article reports on a load testing plan to measure the elasticity of Azure Functions Premium when put under heavy load with a fast ramp-up rate.

Use case:
This use case is based on a real life scenario in the media industry. A web hosted platform that must be able to accept a high volume of HTTP Get requests and be able to scale very rapidly. Traffic originating from consumers' devices and web browsers.

The test aim to find out how quickly can Azure Function Premium scale without losing any requests (100% http-200 response)

Tested scenario: scale from 0 to 10 000 http requests per second (10K rps)

Changing parameter: duration for the 0 to 10K rps ramp-up. This defines the number of new requests per second the Azure Function can receive. We try to capture the point at which the number of errors becomes un-acceptable on a usability point of view. Ramp-up over 2 mins, 1 min, 30 seconds, 20 seconds etc.

<style>
th, td {
  padding: 5px;
}
</style>
<table style="width:100%">
  <tr>
    <th>Test id</th>
    <th>Config</th>
    <th>Req/sec</th>
    <th>Ramp-up</th>
    <th>Duration</th>
    <th>Client/sec</th>
    <th>Fail/Sample(1)</th>
    <th>Avg rps</th>
    <th>AzFunc instances</th>
    <th>EH Incoming Messages</th>
    <th>Test Setup</th>
    <th>Test report<th>
  </tr>
  <tr>
    <td>15/04/2021 13:15:43 (K)</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>2 mins</td>
    <td>4 mins</td>
    <td>83</td>
    <td>1/1.7m</td>
        <td></td>
    <td>15</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>15/04/2021 12:45:44 (K)</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>1 min</td>
    <td>4 mins</td>
    <td>166</td>
    <td>0/1.7m</td>
            <td></td>
    <td>15</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>16/04/2021-17:15:13-(V)</td>
    <td>2</td>
    <td>0 to 10K rps</td>
    <td>1 min</td>
    <td>4 mins</td>
    <td>166</td>
    <td>2/1.63m</td>
            <td>8500</td>
    <td>?</td>
    <td></td>
    <td></td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/16042021_171513_(V)/artifacts/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>23/04/2021 07:57:57</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>2/6.282561 million</td>
            <td>8057</td>
    <td>20</td>
    <td>6.282559 million</td>
    <td>500 Virtual Users x 20 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_075757/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>23/04/2021 08:34:33</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>45/6.293572 million</td>
            <td>8345</td>
    <td>20</td>
    <td>6.293558 million</td>
    <td>500 Virtual Users x 20 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_083433/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>23/04/2021 09:54:49</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>0/6.336730 million</td>
            <td>9496</td>
    <td>16</td>
    <td>6.336730 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_095449/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>23/04/2021 10:34:32</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>0/6.346183 million</td>
            <td>9515</td>
    <td>17</td>
    <td>6.346183 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_103432/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 06:52:13</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>50 sec</td>
    <td>11 mins</td>
    <td>200</td>
    <td>1/6.343606 million</td>
            <td>9535</td>
    <td>13</td>
    <td>6.343606 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_065214/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 07:23:46</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>50 sec</td>
    <td>11 mins</td>
    <td>200</td>
    <td>0/6.357121 million</td>
            <td>9555</td>
    <td>17</td>
    <td>6.357122 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_072346/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 07:53:10</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>40 sec</td>
    <td>11 mins</td>
    <td>250</td>
    <td>0/6.364264 million</td>
            <td>9567</td>
    <td>16</td>
    <td>6.364425 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_075310/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 09:01:05</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>40 sec</td>
    <td>11 mins</td>
    <td>250</td>
    <td>0/6.406986 million</td>
            <td>9633</td>
    <td>13</td>
    <td>6.406986 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_090105/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 09:42:02</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>30 sec</td>
    <td>11 mins</td>
    <td>333</td>
    <td>0/6.448748 million</td>
            <td>9693</td>
    <td>14</td>
    <td>6.448748 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_094202/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 10:20:49</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>30 sec</td>
    <td>11 mins</td>
    <td>333</td>
    <td>0/6.442250 million</td>
            <td>9683</td>
    <td>20</td>
    <td>6.442250 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_102049/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 11:06:09</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>20 sec</td>
    <td>11 mins</td>
    <td>500</td>
    <td>0/6.497785 million</td>
            <td>9769</td>
    <td>15</td>
    <td>6.497785 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_110609/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 13:15:14</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>20 sec</td>
    <td>11 mins</td>
    <td>500</td>
    <td>0/6.468643 million</td>
            <td>9721</td>
    <td>12</td>
    <td>6.468643 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_131514/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 14:17:47</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>10 sec</td>
    <td>11 mins</td>
    <td>1000</td>
    <td>272/6.490735 million</td>
            <td>9756</td>
    <td>13</td>
    <td>6.490463 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_141747/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 15:20:49</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>10 sec</td>
    <td>11 mins</td>
    <td>1000</td>
    <td>0/6.479702 million</td>
            <td>9742</td>
    <td>13</td>
    <td>6.479702 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_152049/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 16:22:25</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>10 sec</td>
    <td>11 mins</td>
    <td>1000</td>
    <td>1/6.381744 million</td>
            <td>9595</td>
    <td>20</td>
    <td>6.381743 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_162225/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 18:00:03</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>0 sec</td>
    <td>11 mins</td>
    <td>10000</td>
    <td>1/6.376057 million</td>
            <td>9578</td>
    <td>17</td>
    <td>5.776255 million (large discrepancy due to Azure Diagnostics missing a sample)</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_180003/dashboard/index.html">Report</a></td>
  </tr>
  <tr>
    <td>24/04/2021 18:57:33</td>
    <td>1</td>
    <td>0 to 10K rps</td>
    <td>0 sec</td>
    <td>11 mins</td>
    <td>10000</td>
    <td>179/6.379544 million</td>
            <td>9585</td>
    <td>17</td>
    <td>6.379365 million</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_185733/dashboard/index.html">Report</a></td>
  </tr>
</table>

(1) Fail/Sample = number of failed requests / sample. Request in unit and requests in millions.

## Azure configuration

EP3 = 840 ACU, 14GB Memory Dv2-Series.

<table style="width:100%">
  <tr>
    <th>Config Id</th>
    <th>Az FD</th>
    <th>BackEnds</th>
    <th>AzF Size</th>
    <th>AzF Max instances</th>
    <th>AzEH Tier</th>
    <th>AzEH Scale</th>
    <th>AzEH Hub Partitions</th>
  </tr>
  <tr>
    <td>1</td>
    <td>No</td>
    <td>n/a</td>
    <td>EP3</td>
    <td>100</td>
    <td>Standard</td>
    <td>20</td>
    <td>32</td>
</tr>
  <tr>
    <td>2</td>
    <td>Yes</td>
    <td>2</td>
    <td>EP3</td>
    <td>100</td>
    <td>Standard</td>
    <td>20</td>
    <td>32</td>
  </tr>

</table>