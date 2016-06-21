# appnext.createAd()

|                      | &nbsp; 
| -------------------- | ---------------------------------------------------------------
| __Type__             | [Function](http://docs.coronalabs.com/api/type/Function.html)
| __Library__          | [appnext.*](Readme.markdown)
| __Return value__     | [String](http://docs.coronalabs.com/api/type/String.html)
| __Keywords__         | ads, advertising, appnext, createAd
| __See also__         | [appnext.loadAd()](loadAd.markdown), [appnext.showAd()](showAd.markdown)


## Overview

This function is used to create an ad with a specific type and placement ID. If an ad with the same type and placement ID already exist it will not be recreated.


## Syntax

	appnext.createAd( adType, placementID )
	appnext.createAd( adType, placementID, configParams )

##### adType <small>(required)</small>
_[String](http://docs.coronalabs.com/api/type/String.html)._ The type of the ad. Possible values: "interstitial", "fullscreen", "rewarded".

##### placementID <small>(required)</small>
_[String](http://docs.coronalabs.com/api/type/String.html)._ The type of the ad. Possible values: "interstitial", "fullscreen", "rewarded".

##### configParams <small>(optional)</small>
_[Table](http://docs.coronalabs.com/api/type/Table.html)._ A Lua table with configuration parameters for the created ad.
Possible configuration parameters and their values vary for different ad types:
* "Categories"  - Set preferred ad categories.
* "Postback"    - Postback parameters that will be posted to your server after user installed an app (make sure to encode the values).
* "ButtonText"  - The install button's text (default is "Install").
* "ButtonColor" - The install button's color - a 6 hex chars starting with #.
* "BackButtonCanClose" - Android only. [Boolean](http://docs.coronalabs.com/api/type/Boolean.html) "Back" key can close the ad (default is 'false').
* "Mute" - [Boolean](http://docs.coronalabs.com/api/type/Boolean.html) Mute the video which is played in the ad (default is 'false').

Interstitial Ads only:
* "CreativeType" - Set creative type for the main section of the Interstitial (default is "managed"). Possible values: "managed", "video", "static".
* "SkipText" - Set a custom text for the "skip" button (default is "Skip").
* "AutoPlay" - [Boolean](http://docs.coronalabs.com/api/type/Boolean.html) Set video auto-play (default is 'true').

Full-Screen/Rewarded Ads only:
* "ProgressType" - Choose progress type, or hide it (default is "clock"). Possible values:"clock", "bar", "none", "default".
* "ProgressColor" - Set progress bar / clock color. 6 characters hex starting with #.
* "VideoLength" - Set video length - 15 or 30 seconds long (default is 15). Possible values:"15", "30", "default".
* "ShowClose" - [Boolean](http://docs.coronalabs.com/api/type/Boolean.html) Display or hide the "x" (close) button.
* "CloseDelay" - [Number](http://docs.coronalabs.com/api/type/Number.html) If the "x" close button is shown, delays its appearance by the set number of seconds.
* "PreferredOrientation" - Set the preferred orientation if both landscape and portrait are supported by the application (default is "automatic"). Possible values:"automatic", "landscape", "portrait".

Rewarded Ads only:
* "RewardsTransactionId" - Make sure to set a unique transaction ID per ad view
* "RewardsUserId" - Pass the User ID so you will know which user to reward.
* "RewardsRewardTypeCurrency" - Type of reward (life / credit / points).
* "RewardsAmountRewarded" - The amount of currency that was rewarded.
* "RewardsCustomParameter" - Pass any custom value / data.


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

local interstitialConfig = {
	SkipText = "Close Ad",
    CreativeType = "video",
}

local videoConfig = {
	ShowClose = true,
    CloseDelay = 5.5,
}

interstitialAdKey = appnext.createAd( "interstitial", interstitialPlacementID, interstitialConfig )
fullscreenAdKey = appnext.createAd( "fullscreen", fullscreenPlacementID, videoConfig )
rewardedAdKey = appnext.createAd( "rewarded", fullscreenPlacementID )
``````
