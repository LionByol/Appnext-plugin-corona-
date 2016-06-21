# appnext.init()

|                      | &nbsp; 
| -------------------- | ---------------------------------------------------------------
| __Type__             | [Function](http://docs.coronalabs.com/api/type/Function.html)
| __Library__          | [appnext.*](Readme.markdown)
| __Return value__     | None
| __Keywords__         | ads, advertising, appnext, init
| __See also__         | [adEvent](adEvent.markdown)


## Overview

This function is used for initializing the listener for all the plugin events.


## Syntax

	appnext.init( listener )

##### listener <small>(required)</small>
_[Listener]()._ Listener type function receiving all the created ads events. Corresponding to [plugin.appnext.adEvent](plugin.appnext.adEvent.markdown).


## Examples

``````lua
local appnext = require 'plugin.appnext'

local function listener( event )
	print( "Received " .. event.event .. " for " .. event.adKey .. " with message:" .. event.message )
end

appnext.init( listener )
``````
