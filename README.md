# rest_client

Use rest_client gem to perform Bing search.

My solution to the Odin Project's ["Rails: Let's Get Building" exercise](https://www.theodinproject.com/courses/ruby-on-rails/lessons/let-s-get-building).

## bing.rb

Requires the rest_client gem.

Contains one BingSearch class which takes the arguments 'url' and 'query' and then runs <code>@data = RestClient.get(url, {:params => {:q => query}})</code>, on initialization of an instance.

The BingSearch class contains 2 functions; One to parse and print out the urls returned in the body of the search, and one to display the raw data returned in the headers, cookies and body.

### Note: This app will return the header, cookies and body from any url (if any exist), not just Bing.com, when <code>BingSearch.print_data</code> is called. <code>BingSearch.print_links</code>, however, will probably return strange results if not run against a query to Bing.com, as it uses strings specific to the body of a Bing search to parse the links returned in the body.

## example

Using the following variable values:

<code>url = 'https://www.bing.com/search'</code><br>
<code>query = 'spaceship'</code><br>

An instance of the BingSearch class is created:
<code>search = BingSearch.new(url, query)</code><br>

Output of calling <code>search.print_links</code>:<br>
<br>
<code>
https://www.merriam-webster.com/dictionary/spaceship<br>
https://en.wikipedia.org/wiki/Spaceship<br>
https://dictionary.cambridge.org/dictionary/english/spaceship<br>
https://www.thefreedictionary.com/spaceship<br>
https://www.ebay.co.uk/bhp/spaceship<br>
https://en.oxforddictionaries.com/definition/spaceship<br>
https://www.spaceshipsrentals.co.uk/<br>
https://www.youtube.com/watch?v=7TYJyCCO8Dc<br>
http://www.argos.co.uk/search/spaceship/<br>
https://www.youtube.com/watch?v=vTV4mr94ijk<br>
<br></code>
