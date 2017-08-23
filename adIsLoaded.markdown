# appnext.adIsLoaded()

|                      | &nbsp; 
| -------------------- | ---------------------------------------------------------------
| __Type__             | [Function](http://docs.coronalabs.com/api/type/Function.html)
| __Library__          | [appnext.*](Readme.markdown)
| __Return value__     | [Boolean](http://docs.coronalabs.com/api/type/Boolean.html)
| __Keywords__         | ads, advertising, appnext, adIsLoaded
| __See also__         | [appnext.loadAd()](loadAd.markdown)


## Overview

This function is used to check if an ad previously created with [appnext.createAd()](createAd.markdown) and loaded with [appnext.loadAd()](loadAd.markdown) is already loaded.


## Syntax

	appnext.adIsLoaded( adKey )

##### adKey <small>(required)</small>
_[String](http://docs.coronalabs.com/api/type/String.html)._ The ad key received previously from [appnext.createAd()](createAd.markdown).


## Examples

``````lua
local appnext = require 'plugin.appnext'

local function listener( event )
	print( "Received " .. event.event .. " for " .. event.adKey .. " with message " .. event.message )
end

-- Initialize the Appnext plugin
appnext.init( listener )

-- Create your Ads
local interstitialPlacementID
local fullscreenPlacementID
local rewardedPlacementID

local platform = system.getInfo( "platformName" )
if ( platform == "iPhone OS" ) then
    interstitialPlacementID = "YOUR_IOS_INTERSTITIAL_PLACEMENT_ID"
    fullscreenPlacementID = "YOUR_IOS_FULLSCREEN_PLACEMENT_ID"
    rewardedPlacementID = "YOUR_IOS_REWARDED_PLACEMENT_ID"
elseif ( platform == "Android" ) then
    interstitialPlacementID = "YOUR_ANDROID_INTERSTITIAL_PLACEMENT_ID"
    fullscreenPlacementID = "YOUR_ANDROID_FULLSCREEN_PLACEMENT_ID"
    rewardedPlacementID = "YOUR_ANDROID_REWARDED_PLACEMENT_ID"
end

interstitialAdKey = appnext.createAd( "interstitial", interstitialPlacementID )
fullscreenAdKey = appnext.createAd( "fullscreen", fullscreenPlacementID )
rewardedAdKey = appnext.createAd( "rewarded", rewardedPlacementID )

appnext.loadAd( interstitialAdKey )

-- At the point you want to show the interstitial ad
if ( appnext.adIsLoaded( interstitialAdKey ) ) then
	appnext.showAd( interstitialAdKey )
end
``````
