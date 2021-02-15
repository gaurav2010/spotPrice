<h1>This is a Challenge Solution for Santander</h1>

<h3> Solution Feature</h3>

  -   This is Developed using Spring Framework
  
  -   Multiple Queries to Fetch SpotPrice can be done Simultaneously
  
  -   As of now, only 1 Thread can update the price - This can be modified

<h3>Design Decisions</h3>
<h5>Why ConcurrentHashMap is used instead of ReadwriteLock</h5>

  - Concurrent HashMap is used over ReadWriteLock as it performs better read though at the cost of accuracy. There is a possibility especially if the read and write is happening on the same instrumnt that we may miss the value from latest write value. This is because when read is not blocked when write is happeing on same segment 
  
  - If this is an issue - then we should switch to Readwrite lock. It will have performance implications as we will be blocking all read threads when the write is happening 

<h5>For ConcurrentHashMap Why none of the parameters was initialised</h5>
  
  - This is dependent upon the data-set and hence best left default for now. This should be changed after we understand the data-set more  
  

<h3>The Solution can be tested as below</h3> 
  
  - Do Maven build and run SpotPriceApplication - Go to browser and open url http://localhost:3001/spotPrice?instrumentName=EUR/GBP
  
  - Run Test class SpotPriceApplicationTests that tests against the Controller - This test also inputs some spot-prices that is used in test
  
  - Run Integration Endpoint test using Test class SpotPriceEndpointIntegrationTest - This test also inputs some spot-prices that is used in test
  
  

