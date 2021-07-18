# Facebook Ads Custom Tracking Installation

This tiny little library allows you to track your facebook campaign ids with your orders.


### Step 1

First copy the codes below and place them right before the closing body tag in your landing page.
```html
<script>
if (window.location.search != '') {
	var fb_campaign_id = '';
	var search_items = window.location.search;
	search_items = search_items.replace('?', '');

	search_items = search_items.split('&&');
	for(i=0;i<search_items.length;i++){
	    var thisItem = search_items[i];
	    if(thisItem.indexOf('utm_medium') > -1){
	        var getCampaign = thisItem.split("=");
	        fb_campaign_id = getCampaign[1];

	        var buyLinkList = document.getElementsByClassName('buyBtn');
			for(i=0;i<buyLinkList.length;i++){
			    var newURL = buyLinkList[i].href+'?attributes[fb_campaign_id]='+fb_campaign_id;
			    buyLinkList[i].href=newURL;
			}

	    }
	}
}
</script>
```

## Step 2
All buy now buttons need to have the class name `buyBtn`
```html
<a href="xxxxx" class="buyBtn XXX XXX XXX">Buy Now</a>
```

## Explanation
It captures the `utm_medium` which is the campaign id ( `https://promo.elevatione.com/us/neck-promo?utm_source=Facebook_Ads&utm_medium={{campaign.id}}&utm_campaign={{adset.id}}&utm_content={{ad.id}}`) and sets as the cart attribute in the buy now button urls.


## License
[MIT](https://choosealicense.com/licenses/mit/)
