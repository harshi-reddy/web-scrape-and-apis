# web-scrape-and-apis
Web Scraping &amp; APIs in Python(Dataquest Course)

An application program interface (API) is a set of methods and tools that allows different applications to interact with each other. Programmers use APIs to query and retrieve data dynamically (which they can then integrate with their own apps). A client can retrieve information quickly and effectively through an API. 

Reddit, Spotify, Twitter, Facebook, and many other companies provide free APIs that enable developers to access the information they store on their servers; others charge for access to their APIs.

#### Pros of APIs:
- The data changes frequently. It doesn't really make sense to regenerate a data set of stock prices, for example, and download it every minute. This approach would require a lot of bandwidth, and be very slow.

- You only want a small piece of a much larger data set. Reddit comments are one example. What if you want to pull just your own comments from reddit? It doesn't make much sense to download the entire reddit database, then filter it for a few items.

- It involves repeated computation. For example, Spotify has an API that can tell you the genre of a piece of music. You could theoretically create your own classifier and use it to categorize music, but you'll never have as much data as Spotify does.

Organizations host their APIs on Web servers. When you type www.google.com in your browser's address bar, your computer is actually asking the www.google.com server for a Web page, which it then returns to your browser.APIs work much the same way, except instead of your Web browser asking for a Web page, your program asks for data. The API usually returns this data in JavaScript Object Notation (JSON) format. We make an API request to the Web server we want to get data from. The server then replies and sends it to us.

