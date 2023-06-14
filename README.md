## Read More button for lengthy text.(show particular no of text, then show rest of the content on Read More button click)

```
jQuery(document).ready(function(){
   var width = jQuery('body').width();
   if(width < 768){
      var maxLength = 500;   // max length of content to display by default
    jQuery(".show-read-more").each(function(){
        var myStr = jQuery(this).text();    // get complete length of text in a variable.
        if(jQuery.trim(myStr).length > maxLength){  // if content length is greater than maxLength
            var newStr = myStr.substring(0, maxLength); // create a new variable from 0 to 500 letters
            var removedStr = myStr.substring(maxLength, jQuery.trim(myStr).length); // create a new varibale from 500 to complete length
            jQuery(this).empty().html(newStr); // remove all text and add only 500 letters as in newStr
            var readmore= 'Read More';
            jQuery(this).append('<div class="for-next-line-read-more"><a class="underlineBtn-2 mobile-readmore" id="read-more-btn-lic">'+readmore+'</a></div>');
            jQuery(this).append('<span class="more-text">' + removedStr + '</span>');
        }
    });
    jQuery("#read-more-btn-lic").click(function(){
        jQuery('.for-next-line-read-more').siblings(".more-text").contents().unwrap();
       jQuery('.for-next-line-read-more').remove();
        jQuery(".show-read-more").removeClass("mobile-read-more-for-gradient");
    });
}
});
```
