# Azure PaaS elasticity load testing

This article reports on a load testing plan to measure the elasticity of Azure Functions Premium when put under heavy load with a fast ramp-up rate.

Use case:
This use case is based on a real life scenario in the media industry. A web hosted platform that must be able to accept a high volume of HTTP Get requests and be able to scale very rapidly. Traffic originating from consumers' devices and web browsers.

The test aim to find out how quickly can Azure Function Premium scale without losing any requests (100% http-200 response)

Tested scenario: scale from 0 to 10 000 http requests per second (10K rps)

Changing parameter: duration for the 0 to 10K rps ramp-up. This defines the number of new requests per second the Azure Function can receive. We try to capture the point at which the number of errors becomes un-acceptable on a usability point of view. Ramp-up over 2 mins, 1 min, 30 seconds, 20 seconds etc.

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
    <td><a target="_blank" href="">Report</a></td>
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
    <td><a target="_blank" href="">Report</a></td>
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
    <td><a target="_blank" href="">Report</a></td>
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
    <td><a target="_blank" href="">Report</a></td>
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