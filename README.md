# REST Server front-end interface for EWD.js Systems: ewdrest
 
This module provides a REST interface to one or more EWD.js systems.

It rewrites incoming REST URLs and rewrites them as signed EWD.js HTTP URLs and routes them
to an EWD.js server where a back-end module provides the web service logic.

Rob Tweed <rtweed@mgateway.com>  
19 June 2013, M/Gateway Developments Ltd [http://www.mgateway.com](http://www.mgateway.com)  

Twitter: @rtweed

Google Group for discussions, support, advice etc: [http://groups.google.co.uk/group/enterprise-web-developer-community](http://groups.google.co.uk/group/enterprise-web-developer-community)


## Installing the REST interface for EWD.js

       npm install ewdrest

	   
## Using the EWD REST Server interface



Define a configuration object that specifies:

- the port on which the REST Server listens;
- the mapping between REST URL and the EWD.js server(s)
- the mapping between REST URL and the back-end EWD.js module(s)

Then start the REST server using this configuration object

  eg:

       var ewdrest = require('ewdrest');

       var params = {
         // REST server listener port
         restPort: 8081,
         // service module mapping
         service: {
           myService: {
             module: 'myModule',
             service: 'parse',
             contentType: 'application/json'
           }
         },
         // EWD.js server mapping
         server: {
           local: {
             host: 'localhost',
             port: 8080,
             ssl: true,
             secretKey: 'TakeARest!',
             accessId: 'RESTServer'
           }
         }
       };
 
       ewdrest.start(params);


Note: the accessId and secretKey must be registered on the EWD.js server, along with any back-end modules 
that requests signed by the accessId are allowed to invoke.  See the chapter on Web Service Interface in
 the EWD.js User Guide.


## License

 Copyright (c) 2014 M/Gateway Developments Ltd,                           
 Reigate, Surrey UK.                                                      
 All rights reserved.                                                     
                                                                           
  http://www.mgateway.com                                                  
  Email: rtweed@mgateway.com                                               
                                                                           
                                                                           
  Licensed under the Apache License, Version 2.0 (the "License");          
  you may not use this file except in compliance with the License.         
  You may obtain a copy of the License at                                  
                                                                           
      http://www.apache.org/licenses/LICENSE-2.0                           
                                                                           
  Unless required by applicable law or agreed to in writing, software      
  distributed under the License is distributed on an "AS IS" BASIS,        
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. 
  See the License for the specific language governing permissions and      
   limitations under the License.      
