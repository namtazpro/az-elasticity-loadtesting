# Azure PaaS elasticity load testing

This article reports on a load testing plan to measure the elasticity of Azure Functions Premium when put under heavy load with a fast ramp-up rate.

Use case:
This use case is based on a real life scenario in the media industry. A web hosted platform that must be able to accept a high volume of HTTP Get requests and be able to scale very rapidly. Traffic originating from consumers' devices and web browsers.

The test aim to find out how quickly can Azure Function Premium scale without losing any requests (100% http-200 response)

Tested scenario: scale from 0 to 10 000 http requests per second (10K rps)

Changing parameter: duration for the 0 to 10K rps ramp-up. This defines the number of new requests per second the Azure Function can receive. We try to capture the point at which the number of errors becomes un-acceptable on a usability point of view. Ramp-up over 2 mins, 1 min, 30 seconds, 20 seconds etc.


<table>
  <tr>
    <th>Test id</th>
    <th>Ramp-up</th>
    <th>Duration</th>
    <th>Client/sec</th>
    <th align="left">- Sample<br>- Fail<br>- EH msgs</th>
    <th>Avg rps</th>
    <th>AzFunc instances</th>
    <th>Test Setup</th>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_075757/dashboard/index.html">23/04/2021 07:57:57</a></td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>6.282561m<br>2<br>6.282559m</td>
    <td>8057</td>
    <td>20</td>
    <td>500 Virtual Users x 20 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_083433/dashboard/index.html">23/04/2021 08:34:33</a></td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>6.293572m<br>45<br>6.293558m</td>
            <td>8345</td>
    <td>20</td>
    <td>500 Virtual Users x 20 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_095449/dashboard/index.html">23/04/2021 09:54:49</a></td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>6.336730m<br>0<br>6.336730m</td>
            <td>9496</td>
    <td>16</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/23042021_103432/dashboard/index.html">23/04/2021 10:34:32</a></td>
    <td>1 min</td>
    <td>11 mins</td>
    <td>166</td>
    <td>6.346183m<br>0<br>6.346183m</td>
            <td>9515</td>
    <td>17</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_065214/dashboard/index.html">24/04/2021 06:52:13</a></td>
    <td>50 sec</td>
    <td>11 mins</td>
    <td>200</td>
    <td>6.343606m<br>1<br>6.343606m</td>
            <td>9535</td>
    <td>13</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_072346/dashboard/index.html">24/04/2021 07:23:46</a></td>
    <td>50 sec</td>
    <td>11 mins</td>
    <td>200</td>
    <td>6.357121m<br>0<br>6.357122m</td>
            <td>9555</td>
    <td>17</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_075310/dashboard/index.html">24/04/2021 07:53:10</a></td>
    <td>40 sec</td>
    <td>11 mins</td>
    <td>250</td>
    <td>6.364264m<br>0<br>6.364425m</td>
            <td>9567</td>
    <td>16</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_090105/dashboard/index.html">24/04/2021 09:01:05</a></td>
    <td>40 sec</td>
    <td>11 mins</td>
    <td>250</td>
    <td>6.406986m<br>0<br>6.406986m</td>
            <td>9633</td>
    <td>13</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_094202/dashboard/index.html">24/04/2021 09:42:02</a></td>
    <td>30 sec</td>
    <td>11 mins</td>
    <td>333</td>
    <td>6.448748m<br>0<br>6.448748m</td>
            <td>9693</td>
    <td>14</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_102049/dashboard/index.html">24/04/2021 10:20:49</a></td>
    <td>30 sec</td>
    <td>11 mins</td>
    <td>333</td>
    <td>6.442250m<br>0<br>6.442250m</td>
            <td>9683</td>
    <td>20</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_110609/dashboard/index.html">24/04/2021 11:06:09</a></td>
    <td>20 sec</td>
    <td>11 mins</td>
    <td>500</td>
    <td>6.497785m<br>0<br>6.497785m</td>
            <td>9769</td>
    <td>15</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_131514/dashboard/index.html">24/04/2021 13:15:14</a></td>
    <td>20 sec</td>
    <td>11 mins</td>
    <td>500</td>
    <td>6.468643m<br>0<br>6.468643m</td>
            <td>9721</td>
    <td>12</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_141747/dashboard/index.html">24/04/2021 14:17:47</a></td>
    <td>10 sec</td>
    <td>11 mins</td>
    <td>1000</td>
    <td>6.490735m<br>272<br>6.490463m</td>
            <td>9756</td>
    <td>13</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_152049/dashboard/index.html">24/04/2021 15:20:49</a></td>
    <td>10 sec</td>
    <td>11 mins</td>
    <td>1000</td>
    <td>6.479702m<br>0<br>6.479702m</td>
            <td>9742</td>
    <td>13</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_162225/dashboard/index.html">24/04/2021 16:22:25</a></td>
    <td>10 sec</td>
    <td>11 mins</td>
    <td>1000</td>
    <td>6.381744m<br>1<br>6.381743m</td>
            <td>9595</td>
    <td>20</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_180003/dashboard/index.html">24/04/2021 18:00:03</a></td>
    <td>0 sec</td>
    <td>11 mins</td>
    <td>10000</td>
    <td>6.376057m<br>1<br>5.776255m (large discrepancy due to Azure Diagnostics missing a sample)</td>
            <td>9578</td>
    <td>17</td>    <td></td>
    <td>250 Virtual Users x 40 Medium Instances</td>
  </tr>
  <tr>
    <td><a target="_blank" href="https://sareportsloadtesting.blob.core.windows.net/testingreports/24042021_185733/dashboard/index.html">24/04/2021 18:57:33</a></td>
    <td>0 sec</td>
    <td>11 mins</td>
    <td>10000</td>
    <td>6.379544m<br>179<br>6.379365m</td>
            <td>9585</td>
    <td>17</td>
    <td>250 Virtual Users x 40 Medium Instances</td>
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