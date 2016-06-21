
# appnext: Plugin API Docs

|                      | &nbsp; 
| -------------------- | ---------------------------------------------------------------
| __Type__             | [Library](http://docs.coronalabs.com/api/type/Library.html)
| __Corona Store__     | [appnext](http://store.coronalabs.com/plugin/appnext)
| __Keywords__         | ads, advertising, appnext
| __See also__         | 

## Overview

The appnext plugin can be used in your [Corona](https://coronalabs.com/products/corona-sdk/) project. It enables you to monetize users through Appnext interstitial, full-screen and rewarded video ads.

## Registration

To use the plugin please register with [Appnext](https://www.appnext.com). Once you get Placement Id(s) for your application you can start creating ads.

## Syntax

	local appnext = require( "plugin.appnext" )

### Functions

##### [appnext.init()](init.markdown)

##### [appnext.getApiVersion()](getApiVersion.markdown)

##### [appnext.createAd()](createAd.markdown)

##### [appnext.loadAd()](loadAd.markdown)

##### [appnext.showAd()](showAd.markdown)

##### [appnext.adIsLoaded()](adIsLoaded.markdown)

##### [appnext.setCategories()](setCategories.markdown)

##### [appnext.getCategories()](getCategories.markdown)

##### [appnext.setPostback()](setPostback.markdown)

##### [appnext.getPostback()](getPostback.markdown)

##### [appnext.setButtonText()](setButtonText.markdown)

##### [appnext.getButtonText()](getButtonText.markdown)

##### [appnext.setButtonColor()](setButtonColor.markdown)

##### [appnext.getButtonColor()](getButtonColor.markdown)

##### [appnext.setBackButtonCanClose()](setBackButtonCanClose.markdown)

##### [appnext.getBackButtonCanClose()](getBackButtonCanClose.markdown)

##### [appnext.setCreativeType()](setCreativeType.markdown)

##### [appnext.getCreativeType()](getCreativeType.markdown)

##### [appnext.setSkipText()](setSkipText.markdown)

##### [appnext.getSkipText()](getSkipText.markdown)

##### [appnext.setAutoPlay()](setAutoPlay.markdown)

##### [appnext.getAutoPlay()](getAutoPlay.markdown)

##### [appnext.setProgressType()](setProgressType.markdown)

##### [appnext.getProgressType()](getProgressType.markdown)

##### [appnext.setProgressColor()](setProgressColor.markdown)

##### [appnext.getProgressColor()](getProgressColor.markdown)

##### [appnext.setVideoLength()](setVideoLength.markdown)

##### [appnext.getVideoLength()](getVideoLength.markdown)

##### [appnext.setCloseDelay()](setCloseDelay.markdown)

##### [appnext.getCloseDelay()](getCloseDelay.markdown)

##### [appnext.setShowClose()](setShowClose.markdown)

##### [appnext.getShowClose()](getShowClose.markdown)

##### [appnext.setMute()](setMute.markdown)

##### [appnext.getMute()](getMute.markdown)

##### [appnext.setPreferredOrientation()](setPreferredOrientation.markdown)

##### [appnext.getPreferredOrientation()](getPreferredOrientation.markdown)

##### [appnext.setRewardsTransactionId()](setRewardsTransactionId.markdown)

##### [appnext.getRewardsTransactionId()](getRewardsTransactionId.markdown)

##### [appnext.setRewardsUserId()](setRewardsUserId.markdown)

##### [appnext.getRewardsUserId()](getRewardsUserId.markdown)

##### [appnext.setRewardsRewardTypeCurrency()](setRewardsRewardTypeCurrency.markdown)

##### [appnext.getRewardsRewardTypeCurrency()](getRewardsRewardTypeCurrency.markdown)

##### [appnext.setRewardsAmountRewarded()](setRewardsAmountRewarded.markdown)

##### [appnext.getRewardsAmountRewarded()](getRewardsAmountRewarded.markdown)

##### [appnext.setRewardsCustomParameter()](setRewardsCustomParameter.markdown)

##### [appnext.getRewardsCustomParameter()](getRewardsCustomParameter.markdown)


### Events

##### [adEvent](adEvent.markdown)

## Project Configuration

### Corona Store Activation

In order to use this plugin, you must activate the plugin at the [Corona Store](http://store.coronalabs.com/plugin/appnext).


### SDK

When you build using the Corona Simulator, the server automatically takes care of integrating the plugin into your project. 

All you need to do is add an entry into a `plugins` table of your `build.settings`. The following is an example of a minimal `build.settings` file:

``````
settings =
{
	plugins =
	{
		-- key is the name passed to Lua's 'require()'
		["plugin.appnext"] =
		{
			-- required
			publisherId = "com.appnext",
			supportedPlatforms = { iphone=true, android=true }
		},
		["plugin.google.play.services"] =
        {
            publisherId = "com.coronalabs",
            supportedPlatforms = { android=true }
        },
	},		
}
``````

### Enterprise

If you have activated this plugin, you can download this plugin from the corresponding plugin page in the [Corona Store](http://store.coronalabs.com/plugin/appnext).


## Platform-specific Notes

> ### Important
> If building for iOS, you must bypass App Transport Security (ATS) by adding the following to the plist table of build.settings. For more information on ATS, please see the [Managing App Transport Security](https://docs.coronalabs.com/daily/guide/hardware/appleATS/index.html) guide.
> ``````
> settings =
> {
>     iphone =
>     {
>         plist =
>         {
>             NSAppTransportSecurity = { NSAllowsArbitraryLoads=true },
>         },
>     },
> }
> ``````


> ### Note
> For Android, the following permissions/features are automatically added when using this plugin:
> ``````
> android =
> {
>     usesPermissions =
>     {
>         "android.permission.INTERNET",
>         "android.permission.ACCESS_NETWORK_STATE",
>     },
> },
> ``````


### Sample Code

You can access sample code [here](SAMPLE_CODE_URL).

### Support

More support is available from the Appnext team:

* [E-mail](mailto://support@appnext.com)
* [Forum](https://community.appnext.com/)
* [Plugin Publisher](https://www.appnext.com)


## Compatibility

| Platform                     | Supported
| ---------------------------- | ---------------------------- 
| iOS                          | Yes
| Android                      | Yes
| Android (GameStick)          | No
| Android (Kindle)             | No
| Android (NOOK)               | No
| Android (Ouya)               | No
| Mac App                      | No
| Win32 App                    | No
| Windows Phone 8              | No
| Corona Simulator (Mac)       | No
| Corona Simulator (Win)       | No

