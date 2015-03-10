What: Adds an "Off" option for the "ServerTokens" directive that causes Apache HTTP Server to no longer send the "Server" header (at all) in any of its responses to client requests.

Why: There is presently no ServerTokens option that can stop Apache from sending information about itself in response headers to client requests. The current options offer variations, but no predefined option stops it entirely. I found Sebastian Nohn implemented the same patch in 2006 against HTTPD 2.0.58, and the Apache PMC consciously decided to not offer this "easy" a manner of turning off the branding, for a variety of reasons.

Where: httpd-2.4.12.ServerTokensOff.patch is in the root of this repository. This has been tested only on Linux, though it should work everywhere.

How:
- Download the file "httpd-2.4.12.ServerTokensOff.patch" from this repository
- Download Apache HTTP Server 2.4.12 source from http://httpd.apache.org/download.cgi#apache24
- Uncompress/extract the contents of the Apache HTTP Server archive
- Apply the patch
- Configure (<-- many Internet tutorials on how to do this) and compile ("make") Apache as you normally would
- Set directive "ServerTokens off" in the httpd.conf file

- Sample commands for a Linux system:
    - wget http://psg.mtu.edu/pub/apache/httpd/httpd-2.4.12.tar.gz <-- Download from one of the mirrors
    - tar xvfz httpd-2.4.12.tar.gz                                 <-- Uncompress/and extract Apache source
    - cd httpd-2.4.12                                              <-- Change to the newly created directory
    - patch -p1 < /location/of/httpd-2.4.12.ServerTokensOff.patch  <-- Apply the patch
    - ./configure { some options usually go here }                 <-- Use any parameters you would ordinarily use
    - make                                                         <-- Compiles a new "httpd" executable

Comments: Instead of patching Apache source code like this one can use mod_security to accomplish this effect
(and much more). See search results of: https://www.google.com/?gws_rd=ssl#q=mod_security+servertokens

Sebastian Nohn's request that his patch be incorporated (includes links to his patch) 
http://mail-archives.apache.org/mod_mbox/httpd-dev/200608.mbox/%3C44D03F79.2030303@nohn.net%3E

Thread of Apache team discussing whether or not to include the patch (they decided not to include it)
http://apache-http-server.18135.x6.nabble.com/vote-on-concept-of-ServerTokens-Off-tt4796590.html#none

You can see the original versions of the relevant source files under directory "httpd-2.4.12"
You can see the modified versions of those relevant source files under directory "httpd-2.4.12.ServerTokensOff"
