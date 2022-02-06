## Http Fundementals


## Dns

Computers use dns servers to find the right ip of a website

`ie: www.google.com = 10.67.8.19`


## Get request

When a computer is requesting a page it uses the http GET request to request a web page and any images, css or javascript that is on that web page


Answer the questions below

What request verb is used to retrieve page content?
`get`

What port do web servers normally listen on?
`80`

What's responsible for making websites look fancy?
`css`



## Verbs/Requests

HTTP has 9 different "verbs" or methods

- POST requests are for sending data to a web server
-- ie: Sending logging in, posting a comment etc,

- GET requests get the web page

There are more verbs but most aren't needed for most web servers

HTTP requests can be broken down into parts

The first line is a verb and a path for the server
`GET /index.html`

## HTTP Headers

Headers give you information on the request. Importantly cookies are sent in the request headers.

Here's and example of a GET request retrieving a simple JS file:

```
GET /main.js HTTP/1.1
Host: 192.168.170.129:8081
Connection: keep-alive
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.122 Safari/537.36
Accept: */*
Referer: http://192.168.170.129:8081/
Accept-Encoding: gzip, deflate
Accept-Language: en-GB,en-US;q=0.9,en;q=0.8
```

## Responses 
The server should reply with a response. Responses follow the same structure as a request but the first line describes the status rather than a verb.

A basic breakdown of the status codes is:
```
    -100-199: Information
    -200-299: Successes (200 OK is the "normal" response for a GET)
    -300-399: Redirects (the information you want is elsewhere)
    -400-499: Client errors (You did something wrong, like asking for something that doesn't exist)
    -500-599: Server errors (The server tried, but something went wrong on their side)
```
More info on status codes here: `https://developer.mozilla.org/en-US/docs/Web/HTTP/Status`


Here is a response of the get request that was shown earlier
```
HTTP/1.1 200 OK
Accept-Ranges: bytes
Content-Length: 28
Content-Type: application/javascript; charset=utf-8
Last-Modified: Wed, 12 Feb 2020 12:51:44 GMT
Date: Thu, 27 Feb 2020 21:47:30 GMT

console.log("Hello, World!")
```


Answer the questions below

What verb would be used for a login?
`post`

What verb would be used to see your bank balance once you're logged in?
`get`

Does the body of a GET request matter? Yea/Nay
`Nay`

What's the status code for "I'm a teapot"?
`418`

What status code will you get if you need to authenticate to access some content, and you're unauthenticated?
`401`

## My cookies 

Cookies are small bits of data that are stored in the browser. Cookies are normally sent with every HTTP request made to a server. Note: That firefox cookies won't work with chrome cookies. Each browser stores them differently.

### Why them cookies

Because HTTP is stateless cookies keep track of stuff. Cookies can be broken down into diffreernt parts. Cookies have the following: Name, value, an expirey date and path

More on cookies: `https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies`

# Mini ctf

## machine ip == 10.10.65.51

## Port == 8081

What's the get flag?
`thm{162520bec925bd7979e9ae65a725f99f}`

```bash
curl http://10.10.65.51:8081/ctf/get
```


What's the POST flag?
`thm{3517c902e22def9c6e09b99a9040ba09}`

```bash
curl -X POST --data 'flag_please' http://10.10.65.51:8081/ctf/post
```

What's the "Get a cookie" flag?
`thm{91b1ac2606f36b935f465558213d7ebd}`

In the cookie section of web dev

What's the "Set a cookie" flag?
`thm{c10b5cb7546f359d19c747db2d0f47b3}`

Set a cookie using web dev tools or curl with the name and value `flagpls`