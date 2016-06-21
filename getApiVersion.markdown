# appnext.getApiVersion()

|                      | &nbsp; 
| -------------------- | ---------------------------------------------------------------
| __Type__             | [Function](http://docs.coronalabs.com/api/type/Function.html)
| __Library__          | [appnext.*](Readme.markdown)
| __Return value__     | [String](http://docs.coronalabs.com/api/type/String.html)
| __Keywords__         | ads, advertising, appnext, getApiVersion
| __See also__         | 


## Overview

Returns the OS Specific SDK version.


## Syntax

	appnext.getApiVersion()


## Examples

``````lua
local appnext = require 'plugin.appnext'
local platform = system.getInfo( "platformName" )
print( "appnextsdk version for " .. platform .. " is: " .. appnext.getApiVersion() )
``````
