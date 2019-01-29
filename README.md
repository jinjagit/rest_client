# rest_client

Use rest_client gem to perform Bing search.

My solution to the Odin Project's ["Rails: Let's Get Building" exercise](https://www.theodinproject.com/courses/ruby-on-rails/lessons/let-s-get-building).

## bing.rb

Requires the rest_client gem.

Contains one BingSearch class which takes the arguments 'url' and 'query' and then runs <code>@data = RestClient.get(url, {:params => {:q => query}})</code>, on initialization of an instance.

The BingSearch class contains 2 functions; One to parse and print out the urls returned in the body of the search, and one to display the raw data returned in the headers, cookies and body.

#### Note:
 This app will return the header, cookies and body from any url (if any exist), not just Bing.com, when <code>BingSearch.print_data</code> is called. <code>BingSearch.print_links</code>, however, will probably return strange results if not run against a query to Bing.com, as it uses strings specific to the body of a Bing search to parse the links returned in the body.

## example

Using the following variable values:

<code>url = 'https://www.bing.com/search'</code><br>
<code>query = 'spaceship'</code><br>

An instance of the BingSearch class is created:
<code>search = BingSearch.new(url, query)</code><br>

Output of calling <code>search.print_links</code>:<br>
<br>
<code>https://www.merriam-webster.com/dictionary/spaceship</code><br>
<code>https://en.wikipedia.org/wiki/Spaceship</code><br>
<code>https://dictionary.cambridge.org/dictionary/english/spaceship</code><br>
<code>https://www.thefreedictionary.com/spaceship</code><br>
<code>https://www.ebay.co.uk/bhp/spaceship</code><br>
<code>https://en.oxforddictionaries.com/definition/spaceship</code><br>
<code>https://www.spaceshipsrentals.co.uk/</code><br>
<code>https://www.youtube.com/watch?v=7TYJyCCO8Dc</code><br>
<code>http://www.argos.co.uk/search/spaceship/</code><br>
<code>https://www.youtube.com/watch?v=vTV4mr94ijk</code><br>
<br>

Output of calling <code>search.print_data</code>:<br>
```text
Headers:
{:cache_control=>"private, max-age=0", :transfer_encoding=>"chunked", :content_type=>"text/html;
 charset=utf-8", :content_encoding=>"gzip", :expires=>"Tue, 29 Jan 2019 17:41:21 GMT",
 :vary=>"Accept-Encoding", :p3p=>"CP=\"NON UNI COM NAV STA LOC CURa DEVa PSAa PSDa OUR IND\"",
 :set_cookie=>["SRCHD=AF=NOFORM; domain=.bing.com; expires=Sun, 23-Feb-2020 17:42:21 GMT; path=/",
 "SRCHUID=V=2&GUID=4DC3AAFA593A468FA74E404144B79FDE&dmnchg=1; domain=.bing.com; expires=Sun,
 23-Feb-2020 17:42:21 GMT; path=/", "SRCHUSR=DOB=20190129; domain=.bing.com; expires=Sun,
 23-Feb-2020 17:42:21 GMT; path=/", "_SS=SID=3663B92028EF6137170DB5D3290360AA; domain=.bing.com;
 path=/", "_EDGE_S=F=1&SID=3663B92028EF6137170DB5D3290360AA; path=/; httponly; domain=bing.com",
 "_EDGE_V=1; path=/; httponly; expires=Sun, 23-Feb-2020 17:42:21 GMT; domain=bing.com",
 "MUID=28FF159ADCCA6860301E1969DD26694A; path=/; expires=Sun, 23-Feb-2020 17:42:21 GMT;
 domain=bing.com", "MUIDB=28FF159ADCCA6860301E1969DD26694A; path=/; httponly; expires=Sun,
 23-Feb-2020 17:42:21 GMT"], :strict_transport_security=>"max-age=31536000; includeSubDomains;
 preload", :x_msedge_ref=>"Ref A: B88A382DA3D84D14B209B23E5CF0DDB6 Ref B: LTSEDGE0521 Ref
 C: 2019-01-29T17:42:21Z", :date=>"Tue, 29 Jan 2019 17:42:21 GMT"}

Cookies:
{"MUID"=>"28FF159ADCCA6860301E1969DD26694A", "MUIDB"=>"28FF159ADCCA6860301E1969DD26694A",
 "SRCHD"=>"AF=NOFORM", "SRCHUID"=>"V=2&GUID=4DC3AAFA593A468FA74E404144B79FDE&dmnchg=1",
 "SRCHUSR"=>"DOB=20190129", "_EDGE_S"=>"F=1&SID=3663B92028EF6137170DB5D3290360AA",
 "_EDGE_V"=>"1", "_SS"=>"SID=3663B92028EF6137170DB5D3290360AA"}

Body:
 <!DOCTYPE html><html lang="en" xml:lang="en" xmlns="http://www.w3.org/1999/xhtml" xmlns:Web=
 "http://schemas.live.com/Web/"><script type="text/javascript" >//<![CDATA[si_ST=new Date//]]>
 </script><head><!--pc--><title>spaceship - Bing</title><meta content="text/html; charset=utf-8"
 http-equiv="content-type" /><meta name="referrer" content="origin-when-cross-origin" /><link
 href="/search?format=rss&amp;q=spaceship" rel="alternate" title="XML" type="text/xml" />

 ... snip (46 pages full of text), snip ...

 [CDATA[var ShareDialogConfig ={"iid":"SERP.5489"};;var ShareDialog;(function(n){function i()
 {t("bootstrap",arguments)}function r(){t("show",arguments)}function u(){t("showError",
 arguments)}functiont(n,t){for(varr=["shdlgapi",n],i=0;i<t.length;i++)r.push(t[i]);sj_evt.
 fire.apply(null,r)}n.bootstrap=i;n.show=r;n.showError=u})(ShareDialog||(ShareDialog={})),
 function(n){function i(){t==0&&u()}function r(){sj_evt.unbind("shdlgapi",i)}function u()
 {t=1;var n="/shared/sdIG="+_G.IG+"&IID="+ShareDialogConfig.iid;n=e(n,["uncrunched",
 "testhooks"]); sj_ajax(n,{callback:function(n,i){n?(t=2,i.appendTo(_d.body),r(),f()):t=3},
 timeout:0})}function f(){var n="rms";_w[n]&_w[n].start()}function e(n,t){var i,r,u;for(r in t)
 u=new RegExp("[?&]"+t[r]+"=[^?&#]*","i"),(i=location.href.match(u))&&i[0]&&(n+="&"+i[0].
 substring(1));return n}function o(){n.inited=0}functions(){n.inited||(n.inited=1,sj_evt
 .bind("shdlgapi",i,!0), sj_evt.bind("ajax.unload",o,!1))}var t=0;s()}(ShareDialog||
 (ShareDialog={}));//]]>--></div><div style="display:none"><!--//<![CDATA
 [Feedback.Bootstrap.InitializeFeedback({page:true},"epf",true,false,false,false,false);;
 0;Feedback.Bootstrap.InitializeFeedback({page:true},"sb_feedback",1,0,0);;//]]>--></div>
 </div><script type="text/javascript" >//<![CDATA[_G.HT=new Date;//]]></script></body></html>
```
