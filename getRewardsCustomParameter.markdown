# appnext.getRewardsCustomParameter()

|                      | &nbsp; 
| -------------------- | ---------------------------------------------------------------
| __Type__             | [Function](http://docs.coronalabs.com/api/type/Function.html)
| __Library__          | [appnext.*](Readme.markdown)
| __Return value__     | [String](http://docs.coronalabs.com/api/type/String.html)
| __Keywords__         | ads, advertising, appnext, getRewardsCustomParameter
| __See also__         | [appnext.setRewardsCustomParameter()](setRewardsCustomParameter.markdown)


## Overview

Relevant for Rewarded ads only. Get the previously set custom parameter value / data for the ad.


## Syntax

	appnext.getRewardsCustomParameter( adKey )

##### adKey <small>(required)</small>
_[String](http://docs.coronalabs.com/api/type/String.html)._ The adKey returned for a previously created ad.


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

appnext.setRewardsCustomParameter( rewardedAdKey, "YOUR_REWARDS_CUSTOM_PARAMETER" )
print( "Custom parameter:" .. appnext.getRewardsCustomParameter( rewardedAdKey ) )
``````
