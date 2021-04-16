# Azure PaaS elasticity load testing

This article reports on a load testing plan to measure the elasticity of Azure Functions Premium when put under heavy load with a fast ramp-up rate.

Use case:
This use case is based on a real life scenario in the media industry. A web hosted platform that must be able to accept a high volume of HTTP Get requests and be able to scale very rapidly. Traffic originating from consumers' devices and web browsers.

The test aim to find out how quickly can Azure Function Premium scale without losing any requests (100% http-200 response)

Tested scenario: scale from 0 to 10 000 http requests per second (10K rps)

Changing paramter: duration for the 0 to 10K rps ramp-up. This defines the number of new requests per second the Azure Function can receive.


<table style="width:100%">
  <tr>
    <th>Test id</th>
    <th>Req/sec</th>
    <th>Ramp-up</th>
    <th>Client / sec</th>
    <th>Errors</th>
    <th>Duration</th>
    <th>Function instances</th>
  </tr>
  <tr>
    <td>15/04/2021 13:15:43 (Kevin)</td>
    <td>0 to 10K rps</td>
    <td>2 mins</td>
    <td>332</td>
    <td>1/1.7m</td>
    <td>3 min</td>
    <td>15</td>
</tr>
  <tr>
    <td>15/04/2021 12:45:44 (Kevin)</td>
    <td>0 to 10K rps</td>
    <td>1 min</td>
    <td>166</td>
    <td>0/1.7m</td>
    <td>3 min</td>
    <td>15</td>
  </tr>
</table>

