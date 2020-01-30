# vue-onepipejs-checkout
[![npm](https://img.shields.io/npm/v/vue-onepipejs-checkout.svg)](https://www.npmjs.com/package/vue-onepipejs-checkout)
[![Github file size](https://img.shields.io/github/size/probil/vue-onepipejs-checkout/dist/vue-onepipejs-checkout.min.js.svg)](https://raw.githubusercontent.com/probil/vue-onepipejs-checkout/master/dist/vue-onepipejs-checkout.min.js)
[![npm](https://img.shields.io/npm/dm/vue-onepipejs-checkout.svg)](https://www.npmjs.com/package/vue-onepipejs-checkout)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/probil/vue-onepipejs-checkout/master/LICENSE)
[![Vue2](https://img.shields.io/badge/Vue-2.x-brightgreen.svg)](https://vuejs.org/)
[![jsDelivr](https://data.jsdelivr.com/v1/package/npm/vue-onepipejs-checkout/badge?style=rounded)](https://www.jsdelivr.com/package/npm/vue-onepipejs-checkout)
[![Tested with TestCafe](https://img.shields.io/badge/tested%20with-TestCafe-2fa4cf.svg)](https://github.com/DevExpress/testcafe)

OnePipe.io is a OneGateway many service. This package implements the the version 2 of  `collect` , `airtime purchase` , `data purchase` service. Check [OnePipe documentation](https://v1.docs.onepipe.io/?version=latest#intro) for more information

## :heavy_check_mark: Browser Support

|![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png) | ![Opera](https://raw.github.com/alrra/browser-logos/master/src/opera/opera_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) | ![iOS Safari](https://raw.github.com/alrra/browser-logos/master/src/safari-ios/safari-ios_48x48.png) | ![Android WebView](https://raw.github.com/alrra/browser-logos/master/src/android-webview-beta/android-webview-beta_48x48.png) | ![Android WebView](https://raw.github.com/alrra/browser-logos/master/src/samsung-internet/samsung-internet_48x48.png)
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 74+ :heavy_check_mark: | 66+ :heavy_check_mark:  | 12+ :heavy_check_mark: | 46+ :heavy_check_mark: | 17+ :heavy_check_mark: | 11+ :heavy_check_mark: | 12+ :heavy_check_mark: | 67+ :heavy_check_mark: | 8.2+ :heavy_check_mark:

We support only browsers with global usage statistics greater then 1%, last 2 version of each browser but not dead browsers. Library may work in older browser but we don't not guarantee that. You may need addition polyfills to make it work. 


## Installation
This version requires Vue 2.X.
```
npm i vue-onepipejs-checkout
```

## Initialization
```
import Vue from 'vue'

// As a plugin
import Checkout from 'onepipe-checkout'
Vue.use(Checkout);

// Or as a directive
import { Checkout } from 'vue-onepipejs-checkout'
Vue.directive('onepipe-checkout', Checkout);

```

### Usage
```
<onepipe-checkout
		size="md"
		:rounded="true"
		api_key="api-key"
		:amount="500"
		request_type="collect"
		:transaction_ref="'123232'"
		:transaction_ref_parent="'parent_123232'"
		transaction_desc="demos payment"
		:customer="customer"
		:options="options"
		:meta="meta"
		:details="details"
		:callback="onCallback"
		:close="onClose"
	>
	Checkout
</onepipe-checkout>
```


## :gear: Configs

List of supported placeholders:

| Value						| Format                       				|
|---------------------------|-------------------------------------------|
| amount					| In kobo Eg 50000                 			|
| api_key					| OnePipe API key                 			|
| request_type     			| collect, airtime purchase, data purchase	|
| close() 	    			| function()								|
| callback() 				| function() 								|
| transaction_desc			| Eg. Sample payment 						|
| transaction_ref   		| Unique Eg. TRX-732423 					|
| transaction_ref_parent   	| TRX-732423								|
| customer  				| Object									|
| details				    | Object 									|
| options				    | Object 									|
| meta 					    | Object 									|
| size 					    | md, sm, lg 								|	
| rounded				    | true, false								|




### Customize configuration
For more details about the configs see [OnePipe Documentation](https://documenter.getpostman.com/view/6358444/SVmySJ79?version=latest#847649c9-eb8a-4038-a916-9bd6b306b435).

