## Version 2.7.0
**Features & Fixes**
* Mission patch PNG size reduced 70-80% using compression (thanks @garyjacobs)
* Added detailed orbital parameters for every payload
* Fixed typo preventing cores from being sorted by number of ASDS launches
* Added list of community made API clients to the readme
* Added `second_stage_block` querystring to allow launch sorting by second stage block number
* Fixed typo preventing travis ci from running tests sequentially, causing long build times
* Readme header updated to only use HTML instead of an HTML/Markdown mix that caused issues on certain viewing platforms
* Added gitlab mirrored repository as a backup
* Added `limit` querystring to limit number of documents returned
* Consolidated past, upcoming, and all launch tests into a single test (DRY)
* Increased jest timeout length from 5sec to 10sec for longer running tests

**Database Changes**
* Added `orbit_params` object to every payload of every past and upcoming launch
* Added `block` number to all second stage objects for hybrid launches
* Added `event_date_unix` to all history milestones for easier date parsing

## Version 2.6.0
**Features & Fixes**
* Added yarn caching for faster Travis builds
* Updated mongo connection syntax to use `async / await`
* Added endpoint for next upcoming launch (thanks @pascoemitch)
* Increased mongo driver connection pool size to prevent traffic surge bottlenecks
* Decreased caching time for launches to 30sec to reduce database query load
* All rocket data now sorted by original launch data instead of rocket id
* Added `/v2/info/history` endpoint with important company milestones
* Added tentative BFR data to rocket endpoints

**Database Changes**
* Added `mission_name` field for easier access to common mission names
* Added `wikipedia` field in `links` for easy access to Wikipedia summaries on launches
* History collection added
* BFR added to list of rockets

## Version 2.5.0
**Features & Fixes**
* Redis route caching times adjusted for quicker launch updates
* Added date format parsing in #80 to allow for any standardized date formats in query strings
* Tests now lint first, allowing for earlier syntax error checks
* Added sorting to rocket endpoints for consistent ordering
* Switched from NPM to Yarn for faster dependency management 
* Removed jest cli option blocking multi worker testing pools
* Moved query logic out of routes and into controllers
* Made all query builders anonymous functions by default

**Database Changes**
* Added `mission_patch_small` filed with links to smaller image versions

## Version 2.4.0
**Features & Fixes**
* Migration from Express to Koa in #78 
* Reduced Docker image size by **~30%** to **19MB**
* Added Redis route caching, reduced average response time from **>250ms** to **<90ms**
* Added Docker-Compose file for easy App + Redis deployment
* Updated all tests to use async/await
* Cap and Core sorting changed to launch date instead of serial in 89ac881
* Reduced npm dependencies by **~10%**

## Version 2.3.0
**Features & Fixes**
* Tests added for query builders in b0b0ad3, f09b3b1, 21c8425 which brings test coverage to 98%
* Abstraction added for fetching upcoming/past launches from a single function e75731e. (Rafael Ramalho)
* Added querystring option to show unique mongo document id's 93610a5
* Added querystring option to filter launches and cores by block number ddd24c7
* Added querystring option to pretty print JSON output for debugging 188cf22
* Added jsdoc for builders and helper functions 3a5d25d

## Version 2.2.0
**Features & Fixes**
* Added current flight number to launch core data
* Dragon data is now on its own endpoint `/v2/capsules`
* Vehicle endpoint is now Rocket endpoint `/v2/rockets` instead of `/v2/vehicles`
* All rocket data has identical schema for easy comparisons
* Added ordering support for past and upcoming launches in #65 
* Updated style guide to Airbnb standards
* Removed needless variable assignments in 4bbe8115482f44dc5601134b15eb265506af5e92
* Some refactoring for mongo driver version 3 breaking changes
    - database url updated to new mongo standard
    - moved projection (used to hide document id from results) out of the find method
* Removed unnecessary files like app.json and single line config file

## Version 2.1.0
**Features & Fixes**
* V2 endpoints with improved filtering and schema added in #61 
* Improved error handling and status code expectations in #51 
* V1 endpoints are now deprecated, and V2 schema was forked from the old DB
* Data validation and custom assertions added in #55 & #58 for better DB consistency and earlier mistake catching thanks to @Srokap 
* Removed double caching bug in #49 
* Added `site_name_long` to all past and future launches in #60

## Version 2.0.2
**Features & Fixes**
* FlightClub.io links are now dynamic in d08fb4ed6a7225e487660daf08855d614f698476 from #43 
* Content type header now shows ```application/json``` in 2a829eb43038fa005833d1c7b096bc36c350d50d from #44 
* 30 minute server DB query caching added in 2f2b819dd7ea03d93a06b61bcbad315fc73cdf46
* Various data typo corrections from #45
* Added CRS data for mass returned, flight time, and cargo manifests from #46 
* Added detailed reuse stats from #47 
* Added endpoints to sort past launches by ASDS or RTLS landings

## Version 2.0.1
**Features & Fixes**
* Endpoint and no results errors now return JSON in lieu of strings
* 404 page removed for faster JSON error responses
* Added endpoint for sorting past launches by launchpad
* Set global content type to application/json for proper headers
* Added more ESlint rules for cleaner javascript

## Version 2.0.0
**Features & Fixes**
* 1:1 platform switch from Sinatra (Ruby) to Express (Node.js) in #42 
* Added Codecov for test coverage monitoring & static code checking
* Test coverage is now 100% 👍 
* Added a "Deploy to Heroku" button as an easy deployment option
* Various typo fixes and formatting errors

## Version 1.2.1
**Features & Fixes**
* Downgraded Puma version to 3.4 to fix issue that prevented docker from starting 1433a57d4a4c416925738b51220df419bf8b049e
* CORS (Cross Origin Resource Sharing) support added in 8d067ca0ef0266224a9eede212eb068ce9d03af6
* Read-Only database credentials are now hard coded to alleviate an issues with testing going forward.
* Various Rubocop fixes throughout
* Travis CI now used container based builds for faster build startup times
* API version support added in 82b2d00af704bf2ed4b148d48bdfd2be7094425f

## Version 1.2.0
**Features & Fixes**
* Falcon 1 data added in fe195477fb07139c23ab567c36d247267874c4cb
* Endpoints refactored for efficiency + better rest standards
* Switched to Puma web server for multiprocess/multithreaded support
* Switched from MySQL to MongoDB for increased data flexibility
* Added sorting filters to mongo queries for readability 535c72d25787bdc81987ffef62ca3afb030ab0cf
* All single object returns now appear without an array 6a892054bb32a4e642f699ccd4117df9b0afce2e & ea8049e5113ea56e776abf5572b3433b1a86a7ea
* Consolidated error messages ea8049e5113ea56e776abf5572b3433b1a86a7ea
* Added latest launches endpoint 598145bef8a52fde06d83df3af874bbca2a58268
* Launches now have links to reddit campaign, launch, recovery, and media threads, as well as official presskit PDF's put out by SpaceX

## Version 1.1.0
**Features & Fixes**
* UTC and Local dates/time are now expressed in ISO 8601 format
* API now has unit tests for Travis CI testing & integration
* Unit tests now have proper subdomain support
* Now using the modular version of Sinatra instead of classic
* Past and Upcoming launches are now in separate tables
* Fixed bug where dates weren't sorting correctly
* Added ability to view all vehicles on a single page
* API now uses routes in line with REST best practices
* Launch site in database is now consistent with launchpads.rb syntax
* Coordinates for launchpads have been corrected
* Various data fixes and corrections

## Version 1.0.4
**Features Added**
* All numerical and boolean data are now given in a primitive form, not as strings

## Version 1.0.3
**Features Added**
* Officially migrated from MySQL to MariaDB to keep with the open source theme
* Mission Patch image links are live
* Added endpoint for upcoming launches

## Version 1.0.2
**Features Added**
* Added data details about booster cores
* Added data details about Dragon capsules
* Added functionality to search launches by capsule and core serial numbers
* Added functionality to search capsule and core details by serial numbers
* Added local time field to launch data (in progress)
* Revised API routes to match up with REST best practices for queries

**Bugfixes**
* Removed strange characters from descriptions for each launch
* Changed array of objects to array of strings in sites.rb

## Version 1.0.1
* API is now live!
* HTTPS has been re-enabled for secure API goodness
* Searching by date is now enabled
* Searching a range of dates is enabled too

## Version 1.0.0
* spacexdata.com is the new domain name
* api endpoints will be api.spacexdata.com
* all static data is fully functional, still working on launch data

## Version 0.0.1
Pre-Release of the SpaceX API

* Still deciding on an appropriate domain name for the endpoints
* Deciding on the proper database for fetching the data
* Base web framework is laid out, but needs data