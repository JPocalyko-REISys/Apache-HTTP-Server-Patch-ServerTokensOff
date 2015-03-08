Implements: Adds an "Off" option for the "ServerTokens" directive that causes Apache HTTP Server
to no longer send the "Server" header (at all) in any of its responses to client requests.

Why: There is presently no ServerTokens option that can stop Apache from sending information about 
itself in response to client requests. The current options offer variations, but no predefined
option stops it entirely. I found Sebastian Nohn implemented the same patch in 2006 against 
HTTPD 2.0.58, and the Apache PMC consciously decided to not offer this "easy" a manner of turning
off the branding.

Comments: Instead of patching Apache source code one can use mod_security to accomplish this effect
(and much more). See search results of: https://www.google.com/?gws_rd=ssl#q=mod_security+servertokens

Sebastian Nohn's request that his patch be incorporated (includes links to his patch) 
http://mail-archives.apache.org/mod_mbox/httpd-dev/200608.mbox/%3C44D03F79.2030303@nohn.net%3E

Thread of Apache team discussing whether or not to include the patch (they decided not to include it)
http://apache-http-server.18135.x6.nabble.com/vote-on-concept-of-ServerTokens-Off-tt4796590.html#none

