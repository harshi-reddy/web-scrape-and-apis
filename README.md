# web-scrape-and-apis
Web Scraping &amp; APIs in Python(Dataquest Course)

# 1. What's an API?
An **Application Program Interface (API)** is a set of methods and tools that allows different applications to interact with each other. Programmers use APIs to query and retrieve data dynamically (which they can then integrate with their own apps). A client can retrieve information quickly and effectively through an API. 

Reddit, Spotify, Twitter, Facebook, and many other companies provide free APIs that enable developers to access the information they store on their servers; others charge for access to their APIs.

#### Pros of APIs:
- The data changes frequently. It doesn't really make sense to regenerate a data set of stock prices, for example, and download it every minute. This approach would require a lot of bandwidth, and be very slow.

- You only want a small piece of a much larger data set. Reddit comments are one example. What if you want to pull just your own comments from reddit? It doesn't make much sense to download the entire reddit database, then filter it for a few items.

- It involves repeated computation. For example, Spotify has an API that can tell you the genre of a piece of music. You could theoretically create your own classifier and use it to categorize music, but you'll never have as much data as Spotify does.

# 2. Introduction to API Requests

Organizations host their APIs on Web servers. When you type www.google.com in your browser's address bar, your computer is actually asking the www.google.com server for a Web page, which it then returns to your browser. APIs work much the same way, except instead of your Web browser asking for a Web page, your program asks for data. The API usually returns this data in JavaScript Object Notation (JSON) format. We make an API request to the Web server we want to get data from. The server then replies and sends it to us. In Python, we use the requests library to do this. 

# 3. Types of Requests

There are many different types of requests. The most common is a GET request, which we use to retrieve data. The server will send a status code indicating the success or failure of your request. You can get the status code of the response from `response.status_code`. 

An API has several API endpoints. An **endpoint** is a server route for retrieving specific data from an API. For example, the `/comments` endpoint on the reddit API might retrieve information about comments, while the `/users` endpoint might retrieve data about users.

```
import requests

response = requests.get("http://api.open-notify.org/iss-now.json")
status_code = response.status_code
```

# 4. Understanding Status Codes

Web servers return status codes every time they receive an API request. A status code provides information about what happened with a request. Some codes that are relevant to GET requests:

- `200` - Everything went okay, and the server returned a result (if any).
- `301` - The server is redirecting you to a different endpoint. This can happen when a company switches domain names, or an endpoint's name has changed.
- `401` - The server thinks you're not authenticated. This happens when you don't send the right credentials to access an API (we'll talk about this in a later mission).
- `400` - The server thinks you made a bad request. This can happen when you don't send the information the API requires to process your request, among other things.
- `403` - The resource you're trying to access is forbidden; you don't have the right permissions to see it.
- `404` - The server didn't find the resource you tried to access.







