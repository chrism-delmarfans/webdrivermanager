# Changelog

## [3.6.0] - 2019-05-17
### Added
- Read chromedriver LATEST_RELEASE page when not using useBetaVersions() (issues #333, #341, #342)

### Fixed
- Enable Edge Dev test (issue #337)

### Changed
- Increase default value of TTL to 86400 seconds (i.e. one day)
- Change changelog format to Markdown (issue #331)


## [3.5.0] - 2019-05-05
### Added
- Support for msedgedriver (Edge based on Chromium)
- Allow WDM_ARCHITECTURE environment values (32, 64) in addition to the new ones (issue #334)
- Set msedgedriver version 75.0.137.0 for Edge 75 in versions.properties
- Set chromedriver version 75.0.3770.8 for Chrome 75 in versions.properties

### Fixed
- Fix Edge support, broken due to changes in web page (issues #335 #338 #339)

### Changed
- Rename version for Edge 44 as pre-installed


## [3.4.0] - 2019-03-27
### Added
- Allow global configuration with method globalConfig() (issue #313)
- Include clearCache() method in WebDriverManager API to clear cache
- Set chromedriver version 73.0.3683.68 for Chrome 73 in versions.properties
- Set chromedriver version 74.0.3729.6 for Chrome 74 in versions.properties

### Changed
- Improve logging when driver version in unknown


## [3.3.0] - 2019-02-06
### Added
- Force using mirror when first exception happens, e.g. 403 error (issue #302)
- Include version.properties URL as configuration key
- Set chromedriver version 2.46 for Chrome 71, 72, and 73 in versions.properties
- Include geckodriver version 0.24.0 for Firefox 65 in versions.properties
- Include operadriver version 2.42 for Opera 58 in versions.properties

### Changed
- Improve cache handling for retries


## [3.2.0] - 2019-01-07
### Added
- Update versions.properties: Chrome 72; Firefox 64; Opera 57
- Use single configuration instance per driver manager singleton
- Read beta versions for driver from versions.properties
- Read also https_proxy (in lower case) from environemnt variables (issue #292)
- Add method to clear preferences in WebDriverManagager API

### Fixed
- Fix issue #296 (Chrome version not being detected on Windows)

### Changed
- Change preference key format to browser name plus version (e.g. chrome69)
- Use local (online if not found) versions.properties for stable and online (always) for beta versions


## [3.1.1] - 2018-12-10
### Added
- Update versions.properties: Opera 57

### Fixed
- Bug-fix: browser binary path for Linux and Mac was not correctly set


## [3.1.0] - 2018-12-09
### Added
- Store resolved latest versions as Java preferences with a time to live (ttl, by default 60 seconds)
- Reading versions.properties from GitHub if browser version not found in local
- Read Windows program file env depending on the platform (32|64 bits)
- Implement manager to download selenium-server-standalone jar files
- Support for Edge 44 (insiders)
- New API methods: ttl(), browserPath()
- Include clear-preferences option in CLI
- Update versions.properties: Chrome 68, 69, 70, 71; Firefox 63; Opera 56; Edge 44

### Changed
- Using default properties is some value is missing


## [3.0.0] - 2018-07-04
### Added
- Auto driver check for Chrome in Window, Linux, and Mac
- Auto driver check for Firefox in Window, Linux, and Mac
- Auto driver check for Opera in Window, Linux, and Mac
- Auto driver check for Edge in Window
- WebDriverManager Server

### Changed
- Set minimum Java compatibility version to 1.8

### Removed
- Drop compatibility with 1.x API, i.e. DriverManager.getInstance()

### Deprecated
- Use a unique name for driver name (deprecate the use of wires for Firefox)


## [2.2.5] - 2018-08-16
### Fixed
- Bug-fix: logic for checking drivers in cache (issue #232)

### Changed
- Improve cache logic (issue #229)


## [2.2.4] - 2018-07-04
### Fixed
- Bug-fix: Filter by driver name when seeking binaries in cache (issue #223)


## [2.2.3] - 2018-06-21
### Fixed
- Bug-fix: Avoid filtering by OS in the case of IEDriverServer
- Bug-fix: Update EdgeDriverManager due to changes in web repository


## [2.2.2] - 2018-06-08
### Changed
- Improve cache handling (issue #216)
- Remove unnecessary reverse of URL lists (issue #206)
- Exclude logback-classic from compile scope (issue #202)


## [2.2.1] - 2018-04-09
### Added
- Force architecture filtering when explicit setup (issue #200)
- Keep latest version value by manager instance (issue #197)

### Changed
- Clean Downloader logic and logging
- Rename operativeSystem() method to operatingSystem() (issue #196)
- Move post downloader logic for Edge binary into the proper manager


## [2.2.0] - 2018-03-23
### Added
- Configuration manager: WebDriverManager.config()
- Interactive mode #1: mvn exec:java -Dexec.args="browserName"
- Interactive mode #2: java -jar webdrivermanager.jar browserName
- Create fat-jar from source code: mvn compile assembly:single
- Method getVersions() to get all driver versions available (issue #191)

### Fixed
- Bug-fix: intermittently fails to download driver when running in parallel (issue #186)
- Bug-fix: Improve exit condition looking for binary file in post download logic (issues #193 and #194)
- Bug-fix: honor forceDownload() option (related to issue #186)

### Removed
- Remove envs WDM_GIT_HUB_TOKEN_NAME and WDM_GIT_HUB_TOKEN_SECRET (use WDM_GITHUBTOKENNAME and WDM_GITHUBTOKENSECRET instead)


## [2.1.0] - 2018-01-04
### Added
- Include class diagram using ObjectAid

### Changed
- Use multiton pattern (WebDriverManager class) to provide unique access point
- Keep getInstance() method for backwards compatibility, e.g. ChromeDriverManager.getInstance().setup();
- Rename forceOperativeSystem() method to operativeSystem()
- Rename useTaobaoMirror() method by useMirror()
- Remove logback.xml from packaged jar (issue #181 and #184)
- Change configuration key wdm.forceOs by wdm.os


## [2.0.1] - 2017-12-12
### Added
- Include configuration key wdm.forceOs to force operative system
- Include configuration keys wdm.proxy, wdm.proxyUser, and wdm.proxyPass for proxy settings
- Include configuration key wdm.useTaobaoMirror to use Taobao mirror

### Changed
- Configuration keys (wdm.*) are now optional (default values: false, "", 0)


## [2.0.0] - 2017-11-27
### Added
- New method in BrowserManager API: forceOperativeSystem(OperativeSystem operativeSystem)
- New method in BrowserManager API: ignoreVersions(String... versions)
- Use logback instead of simplelogger for logging
- Use SonarCloud to keep a good level of internal code quality
- Use Codecov to keep a good level of code coverage
- Reset state of browser managers after setup

### Changed
- Relicense to Apache 2.0
- Stop using tyepsafe config library for handling properties
- Override configuration values with environmental variables (e.g. WDM_TARGETPATH)
- Improve management of proxy
- Upgrade to Selenium 3.7 for end-to-end tests
- Improve test performance

### Removed
- Remove deprecated methods from version 1.x (MarionetteDriverManager, etc)


## [1.7.2] - 2017-09-17
### Added
- Add wdm.architecture configuration key (issue #154)
- Read properties values from system environment as fallback to properties


## [1.7.1] - 2017-07-10
### Added
- Use NTCredentials for NTLM AuthSchemes (PR #149 from andrew-sumner)
- Avoid throwing exception in the case of non supported managers (e.g. RemoteWebDriver)

### Changed
- Improve support for new versions of operadriver (e.g. 2.27 and 2.29)


## [1.7.0] - 2017-06-18
### Added
- Automatic retry forcing the use of cache on exception (issue #125)
- Skip beta versions by default (issue #127 and #136)
- Added getBinaryPath() method to BrowserManager API
- Prevent non-executable files being picked as driver executables (PR #133 from Konfuzzyus)

### Fixed
- Bug-fix: added connection manager shared (PR #140 from tharakadesilva)
- Bug-fix: Improve support for Edge (issue #135)
- Bug-fix: Support for latest version of operadriver (issues #134 and #146)

### Changed
- Format code with spaces instead of tabs

### Removed
- Remove guava, commons-codec dependencies


## [1.6.2] - 2017-04-04
### Added
- New method in BrowserManager API: forceDownload()
- Support proxy server with authentication (isee #118, PR #120 by kazuki43zoo)
- Checking that binary files are actually executable (issue #114 and #121)

### Fixed
- Bug-fix: issue #115 number format exception due to IEDriver beta
- Bug-fix: issue #116 Ensure files aren't folders to check distro name

### Changed
- Downgrade com.typesafe:config to 1.2.1 (for Java 7 compliance)
- Ignore Taobao test due to connection reset error


## [1.6.1] - 2017-03-08
### Added
- New method in BrowserManager API: proxy()

### Fixed
- Bug-fix: forceCache() method was not working properly


## [1.6.0] - 2017-02-07
### Added
- Support for taobao.org mirror in FirefoxDriverManager
- Support for taobao.org mirror in ChromeDriverManager
- Expose BrowserManager API following the builder pattern
- New methods in BrowserManager API: version(), forceCache(), architecture(Architecture), arch32(), arch64(), useTaobaoMirror(), driverRepositoryUrl(URL)

### Deprecated
- Deprecate setup method with parameters (now builder pattern is used)


## [1.5.1] - 2017-01-19
### Added
- Allow running in separate classloader (PR #83 from phillcunnington)
- Improve download internal logic (add pre/post download methods)

### Fixed
- Bug-fix: update EdgeDriverManager (PR #87 from oscarcarlsson)
- Bug-fix: support for PhantomJS 2.5.0-beta (issue #96)

### Changed
- Change default URL for PhantomJS from npm.taobao.org to bitbucket.org
- Change default URL for PhantomJS from npm.taobao.org to bitbucket.org


## [1.5.0] - 2016-11-15
### Fixed
- Issue #77: bug-fix for phantomjs 32-bit artifact

### Changed
- Change default name of properties file to webdrivermanager.properties
- Use of Selenium 3 in internal tests

### Deprecated
- Deprecate MarionetteDriverManager (use instead FirefoxDriverManager)


## [1.4.10] - 2016-10-13
### Added
- Compatibility with Selenium 3
- Support for taobao mirror for chromedriver and  (wdm.chromeDriverUrl=https://npm.taobao.org/mirrors/chromedriver/)
- Support for taobao mirror for operadriver (wdm.operaDriverUrl=https://npm.taobao.org/mirrors/operadriver/)
- Issue #61: Support HTTP proxy by means of env var HTTP_PROXY or HTTPS_PROXY (PR #62 from Sebl29)

### Changed
- Stop using htmlunit to download edge binaries (jsoup instead)


## [1.4.9] - 2016-09-11
### Added
- Issue #52: Force the use of cache when network is not available
- Add Travis support (thanks to PR #57, #58, #59 by hennr)

### Fixed
- Bug-fix issue #19 (regression): getDriverName returns a list of string

### Changed
- Issue #40 and #56: Replace bitbucket PhantomJS source by mirror using jsoup instead HtmlUnit


## [1.4.8] - 2016-08-15
### Fixed
- Bug-fix issue #51: Determine correct geckodriver to download (PR #48 from phillcunnington)


## [1.4.7] - 2016-08-01
### Fixed
- Bug-fix issue #44: Fixed PhantomJS downloads page change (PR #45 from ndtreviv)


## [1.4.6] - 2016-07-01
### Added
- Handle exceptions when parsing URLs, reading next if necessary
- Use unTarGz method if needed


## [1.4.5] - 2016-05-12
### Added
- Support for multiple binary names (caused by geckodriver)
- Key wdm.forceCache to force using the latest version of binaries in cache

### Fixed
- Bug-fix: correct support for Marionette in generic manager

### Changed
- Improve the way of handling the version number of Edge driver


## [1.4.4] - 2016-06-05
### Added
- Include several HTTP headers to connect with server in downloads
- Include token/secret configuration keys for GitHub credentials


## [1.4.3] - 2016-05-10
### Added
- Exception for seeking PhantomJS in the binary cache


## [1.4.2] - 2016-04-05
### Added
- Check that repository target folder exits (otherwise create)
- Honor property (wdm.*Url) if available for driver version

### Fixed
- Bug-fix issue #24: search driver in cache by architecture


## [1.4.1] - 2016-03-12
### Fixed
- Bug-fix issue #19: WDM is unable to download the 64-bit IEDriverServer
- Bug-fix issue #20: PhantomJsDriverManager exception

### Changed
- Change URL to download Edge driver (exe instead of msi)
- Improve compatibility with Microsoft Windows and Mac OS X
- Improve test coverage


## [1.4.0] - 2016-01-13
### Added
- Add PhantomJS support (pull request #13 from wilx/master-phantomjs)
- Add Marionette support (pull request #14 from rosolko:master)

### Changed
- Improve tests


## [1.3.1] - 2015-11-07
### Added
- Check that existing binaries are valid before exporting variable
- Retries when seeking remote URL to find out latest version of binaries

### Changed
- Change log level of important messages to INFO


## [1.3.0] - 2015-11-01
### Added
- Support for Microsoft Edge


## [1.2.4] - 2015-10-20
### Added
- Assess that binary exists in cache to avoid seeking remote server


## [1.2.3] - 2015-09-01
### Fixed
- Bug-fix: redirection of setup call to the proper method


## [1.2.2] - 2015-08-19
### Changed
- Improved automatic discover of latest version to be downloaded (GitHub issue #5)
- Improved test coverage
- Changed log level to DEBUG


## [1.2.1] - 2015-08-14
### Added
- Added getter to read the downloaded version

### Changed
- Improved driver version management


## [1.2.0] - 2019-03-27
### Added
- Thread safe download. Pull request thanks to Ivan Gracia (izanmail@gmail.com)


## [1.1.2] - 2015-07-06
### Changed
- Manager classes as singlentons


## [1.1.1] - 2015-06-23
### Added
- Added provided scope to slf4j-simple

### Fixed
- Bug-fix: store binary in path using version instead of LATEST


## [1.1.0] - 2015-06-23
### Added
- Added parameter to force the use of a concrete WebDriver binary version

### Changed
- Changed log dependency from slf4j-log4j12 to slf4j-simple
- Changed setup from static method to instantiation of DriverManager


## [1.0.1] - 2015-06-09
### Fixed
- Bug-fix: Wrong chromedriver version downloaded (GitHub issue #1)


## [1.0.0] - 2015-03-19
### Added
- Automated download of WebDriver binaries
- Automated export of WebDriver binaries path
- Supported WebDriver binaries: Chrome, Opera, Internet Explorer
- Customizable configuration parameters using Java system properties
- Capability to force WebDriver binary architecture (32/64 bits)
