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

# 5. JSON Format

**JavaScript Object Notation (JSON)** is the primary format for sending and receiving data through APIs. This format encodes data structures like lists and dictionaries as strings to ensure that machines can read them easily. Python offers great support for JSON through its `json` library. We can convert lists and dictionaries to JSON, and vice versa. The JSON library has two main methods:

- `dumps` - Takes in a Python object, and converts it to a string
- `loads` - Takes a JSON string, and converts it to a Python object

# 6. Getting JSON From a Request

We can get the content of a response as a Python object by using the `.json()` method on the response.
```
parameters = {"lat": 37.78, "lon": -122.41}
response = requests.get("http://api.open-notify.org/iss-pass.json", params=parameters)
json_data = response.json() # content of a response
```
# 7. Content Type

The server sends more than a status code and the data when it generates a response. It also sends metadata containing information on how it generated the data and how to decode it. This information appears in the response headers. We can access it using the `.headers` property that responses have.

The headers will appear as a dictionary. The content-type within the headers tells us the format of the response, and how to decode it.
```
print(response.headers)
content_type = response.headers['content-type']
```
###### Output : 
	{'date': 'Sat, 05 Sep 2015 01:49:13 GMT', 'server': 'gunicorn/19.3.0', 'via': '1.1 vegur', 'connection': 'keep-alive', 'content-length': '520', 'content-type': 'application/json'}