# ChallengeTaller
Describing a project of Web, Api and Mobile Automation

1 - The structure will have this following directories. The tests directory would contains the test cases to
all platforms (web, mobile, api). The config structure will have all configuration to run the tests,
including the clients to apis, clients to report the results or other configs to run the tests
in a CI Pipeline. The utils structure can have the methods, data providers. 
The pages (can be other name) structure can have the screens of the mobile and ui tests, 
using the pattern page objects. To manage the dependencies in this project I could use Gradle.

	kotlin
	 - src
	    - utils	
	    - config
	    - pages
	    - tests
		- mobile
		- api
		  -model
		    - request
		    - response	
		- web

2 - To handle the environment I would create config files separated by environment, such as local, qa environment.
The tests will run by environment. To create the model and responses of the requests, I would
create a structure in api structure, where I put the models to be used in the http requests/response. In this case,
I would think in contexts or functions of the api to create the models. About the shared client API, I would create a
specific client to be reused for all aplication. If this API is unavailable sometimes, I would think to
create a mock to have this responses.

3 - To create the web tests I would separate the screens and actions of each page using the Page Object Model, 
focusing oo avoid putting sleeps on the tests, creating a structure with good selectors (to have fast responses of the website),
and limitating the time that I expect for the elements. To run this tests in a remote environment I would create
a Dockerfile with my all dependencies.


4 - The config of mobile tests will contain the main configs to run the tests in different types of devices.
I can integrate the project with BrowserStack to access differents devices, and manage the capabilities according
to to this devices. To create the integration I will need use the Appium and config it.

5 - Thinking on execution of the tests I can separate the tests with tags, like @ApiTests, @WebTests, @MobileTests.
During the execution is possible to have this parameter, like -includetag=api-test. To have this, I need to config
that @ApiTests = api-test. About the environment, I can config profiles to each environment that I have and use it 
as parameter to each execution, for examplo, PROFILE_ACTIVE=local.

6- The pipeline of test could run after some update in mobile, web or api application. Explaining, when a software
engineer create a Pull Request the pipeline could be started by type of tests, for example: integration test, e2e tests,
api tests, web tests. To have the data about the executions, it's possible to send the JUnit results to a platform that 
is responsible to show the results or to send reports to teams or slack.
