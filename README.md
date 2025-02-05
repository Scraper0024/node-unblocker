# node-unblocker
Explore the key limitations of using Node-unblocker for web scraping! Learn about potential solutions and workarounds to enhance scraping efficiency.

Node Unblockers can be customized to include features such as IP rotation, header customization, and encryption. So we are used to building Node unblockers to bypass website blocking.

A Node unblocker does excel in bypassing website challenges, but in practice we find that we still need to deal with some of its inherent troubles.

How to make your Node Unblocker more powerful? Is there a method or tool that can completely overcome website challenges directly?

It's time to find the best answer from this article!

## What Is a Node Unblocker?
Node Unblocker is a web proxy tool built with Node.js that helps bypass network restrictions or website access limitations. It acts as an intermediary between the user and the target website, allowing the user to interact with content that may be blocked due to geo-restrictions, network filters, or firewalls.

Unblockers do this by routing the user's request to a Node.js server, which fetches the desired content and returns it to the user. It generally supports dynamic content handling, making it suitable for modern web applications.

## How to Use Node Unblocker?
First, we will create a basic Node.js service. Then, we’ll discuss how to use Node Unblocker to create middleware, enabling its integration within our Node service. For additional details, you can visit the [Node Unblocker](https://github.com/nfriedly/node-unblocker) documentation directly.

### Prerequisites
Before starting, you need to have Node.js installed. You can download Node.js [here](https://nodejs.org/en/download/).
Now let’s begin by creating a basic Node.js service. 
- Initialize a new Node.js project. If you don’t already have a project, create one using the following commands:
```Bash
mkdir node-unblocker-tutorial
```

- Navigate to the project directory, initialize the project, and install the required dependencies:
```Bash
cd node-unblocker-tutorial
npm init -y
pnpm add express unblocker
```

- Now, create a new file, index.js, to organize your code:
```Bash
touch index.js
```

### Setting Up the Basic Node.js Service
- Import the necessary modules, `express` and `unblocker`:
```JavaScript
import express from 'express';
import unblocker from 'unblocker';
```

- Next, create an Express application:
```JavaScript
const app = express();
```

- Initialize an instance of Unblocker and set its proxy prefix:
```JavaScript
const unblocker = new Unblocker({
    prefix: '/proxy/'
});
```

Make sure to integrate the Unblocker instance with the Express application using the `app.use()` method:
```JavaScript
app.use(unblocker());
```

- Define a port and start the Node.js service using the `app.listen()` method:
```JavaScript
const PORT = process.env.PORT || 9090;
app.listen(PORT, () => {
    console.log(`Server started on port ${PORT}`);
});
```

- Here’s the complete code for the setup:
```JavaScript
import express from 'express';
import Unblocker from 'unblocker';

const app = express();
const unblocker = new Unblocker({ prefix: '/proxy/' });

app.use(unblocker);

const PORT = process.env.PORT || 9090;
app
  .listen(PORT, () => {
    console.log(`Server started on port ${PORT}`);
  })
  .on('upgrade', unblocker.onUpgrade);
```


### Running the Service
Run the `index.js` file using Node to start the server on port 9090. Test the proxy by appending the target URL to the proxy prefix. For this example, we’ll use `https://ident.me/` as the target page. Open the following link in your browser after running the service:
node index.js

You’ll see a page displaying the current service's IP address, indicating that the setup is working correctly:

![current service's IP address](https://assets.scrapeless.com/prod/posts/node-unblocker/2a4090fa91d8a940f2250b0e17a1306e.png)

## 5 Limitations of Node Unblocker
1. **Performance Bottlenecks**

Since Node Unblocker processes web requests and responses in real time, it can become a performance bottleneck when handling a large number of simultaneous requests or heavy traffic.

2. **Resource Consumption**

Node Unblocker requires server resources for handling requests, especially when dealing with large files, multimedia content, or heavily dynamic web pages. This can lead to increased CPU and memory usage.

3. **Limited Bypass Capabilities**

While Node Unblocker can bypass some basic restrictions, it struggles with advanced anti-bot systems like CAPTCHA, JavaScript fingerprinting, or IP-based rate-limiting mechanisms.

4. **Scalability Challenges**

Node Unblocker is not inherently built for distributed setups or high scalability, which makes it less suitable for enterprise-grade or large-scale applications without significant customization.

5. **Lack of HTTPS Inspection**

Node Unblocker does not decrypt or inspect HTTPS traffic, which limits its ability to modify or analyze encrypted data during the proxy process.

## What Are Some of the Best Practices for Using Node Unblocker?
### 1. Rotate user-agent headers
To make your web scraping activities appear as though they originate from different users, it is essential to rotate the User-Agent headers. This practice significantly lowers the likelihood of a website detecting your requests as automated.
### 2. Implement IP rotation
Relying on a single proxy IP is almost as risky as accessing a website directly, as it increases the chances of your IP being flagged or blocked. Implementing IP rotation helps you avoid detection and ensures seamless access to collect the required web data.
### 3. Limit frequency of requests
Rate limiting is a vital measure to prevent your IP from being flagged. Rapidly sending multiple requests from the same IP within a short time frame can trigger a website’s anti-bot protections, potentially leading to a ban. By incorporating delays in your scraping code, you can minimize these risks and maintain smooth operations.
### 4. Error handling
Effective error handling is crucial for successful web scraping. Incorporate mechanisms in your code to address scenarios where the target website does not return the expected response, ensuring your scraping process remains robust and efficient.

## Integrating Scrapeless Web Unlocker for Advanced Features
### Why is Scrapeless effective at avoiding blocks?
Scrapeless Web Unlocker leverages a global network that spans 195 countries, supported by access to over 70 million residential IPs. With a 99.9% uptime and exceptional success rates, Scrapeless easily overcomes challenges like IP blocks and CAPTCHA, making it a robust solution for complex web automation and AI-driven data collection.
### Is Scrapeless costly?
Scrapeless offers a reliable and scalable web scraping platform at competitive prices, ensuring excellent value for its users:
- **Scraping Browser**: From $0.09 per hour
- **Scraping API**: From $1.00 per 1k URLs
- **Web Unlocker**: $0.20 per 1k URLs
- **Captcha Solver**: From $0.80 per 1k URLs
- **Proxies**: $2.80 per GB

By subscribing, you can enjoy discounts of up to 20% on each service. Do you have specific requirements? Contact us today, and we’ll provide even greater savings tailored to your needs!

### Detailed steps to Integrate Scrapeless into Your Project
#### Prerequisites
Before getting started, you need to [**register a Scrapeless account**](https://app.scrapeless.com/passport/register?utm_source=official&utm_medium=blog&utm_campaign=node-unblocker). You can also navigate the [official website](https://www.scrapeless.com/) to learn more about Scrapeless.

Once registered, navigate to the Scrapeless Dashboard and click on the **Web Unlocker** menu on the left panel. Here, you’ll find a variety of configuration options, including Proxy, JS Render, Request Method, and JS Instructions. These features address several limitations of Node Unblocker, and you can customize them according to your requirements.

If you’re unfamiliar with these configuration options, you can [refer to the detailed documentation](https://docs.scrapeless.com/en/web-unlocker/quickstart/introduction/) by clicking the "**Documentation**" link on the page.

![refer to the detailed documentation](https://assets.scrapeless.com/prod/posts/node-unblocker/b57be74762e65a72b32a85100ebd6dce.png)

Scrapeless also provides code samples in three programming languages—Python, Node.js, and Golang. You can choose the language that suits your needs for integration. In this example, we’ll use Node.js.

#### Bypass Captchas
Scrapeless Web Unlocker automatically enables CAPTCHA bypass functionality, eliminating concerns about CAPTCHA challenges. To verify this, first, use Curl to make a request to a site that requires verification, such as:
```Bash
curl https://app.ahrefs.com/user/login
```

In the screenshot below, the Curl request returns a CAPTCHA verification page. You can see the Cloudflare verification details in the response:

![Cloudflare verification](https://assets.scrapeless.com/prod/posts/node-unblocker/a6bafb2c4fea5026fe03ef9b1aa1f9ec.png)

Now, using `Scrapeless Web Unlocker` to request the same site, follow these steps:
- Create a scrapeless-web-unlocker.js file with the following code:
```JavaScript
import fetch from 'node-fetch';

class Payload {
  constructor(actor, input, proxy) {
    this.actor = actor;
    this.input = input;
    this.proxy = proxy;
  }
}

async function sendRequest() {
  const host = 'api.scrapeless.com';
  const url = `https://${host}/api/v1/unlocker/request`;
  const token = ''; // your token

  const inputData = {
    url: 'https://app.ahrefs.com/user/login',
    method: 'GET',
    redirect: false,
  };

  const proxy = {
    country: 'ANY',
  };

  const payload = new Payload('unlocker.webunlocker', inputData, proxy);

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'x-api-token': token,
      },
      body: JSON.stringify(payload),
    });

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const body = await response.text();
    console.log('body', body);
  } catch (error) {
    console.error('Error:', error);
  }
}

sendRequest();
```

- Running the code with `node scrapeless-web-unlocker.js`.
We can see that the Captchas verification has been successfully bypassed in the returned results, and the DOM content of the page has been obtained. In addition, the title "User login - Ahrefs" in the page code can also be successfully retrieved in our results.
![Bypass Captchas](https://assets.scrapeless.com/prod/posts/node-unblocker/96ee93a5c96535c9159021153a974a42.png)

![Bypass Captchas](https://assets.scrapeless.com/prod/posts/node-unblocker/1571d29cb21cc76ea3df94b205003b9b.png)

#### Javascript Rendering
JavaScript rendering can handle dynamically loaded content and single-page applications (SPA). It enables a full browser environment and supports more complex page interactions and rendering requirements. Scrapeless's Web Unlocker service can solve the problem that Node Unblocker cannot execute JavaScript. We can enable the JavaScript Rendering function in Scrapeless's Web Unlocker so that we can get the page content rendered by JavaScript.

We can find a website that uses JavaScript rendering, such as Cloudflare's Dashboard login page. We can see that the framework technology it uses is React.js, and React.js is a single-page application framework, and its content is rendered by JavaScript.

![Javascript Rendering](https://assets.scrapeless.com/prod/posts/node-unblocker/6c3b34f8b4b24b586f414e5053e6f253.png)

Now, let's modify the previous code slightly to see if we can get the content of Cloudflare's Dashboard login page without enabling JavaScript Rendering. Modify the code as follows:
```JavaScript
...
url: 'https://dash.cloudflare.com/login',
...
```

We can see that the div with `id="react-app"` in the returned result is empty, which means that we did not get the page content after JavaScript rendering:

![JavaScript rendering results](https://assets.scrapeless.com/prod/posts/node-unblocker/3e90196c0b4e1134b800a2ff1ffec75e.png)

Next, we turn on the JavaScript Rendering function and modify the code as follows:
```JavaScript
  const inputData = {
    url: 'https://dash.cloudflare.com/login',
    method: 'GET',
    redirect: false,
    js_render: true, // new option
    js_instructions: [ // new option
      {
        wait: 20000,
      },
    ],
  };
```

In the above code, we added two new configuration options, `js_render` and `js_instructions`. For more instruction references, please refer to [Scrapeless Docs](https://docs.scrapeless.com/en/web-unlocker/features/js-render/#javascript-instructions-reference):
- `js_render` is used to turn on the JavaScript Rendering function
- `js_instructions` is used to set the instructions for JavaScript Rendering. Here, we set a 20-second wait instruction to return the result after the page is loaded.

> **Note**: Now many websites have a loading process by default, so we need to wait for a while to ensure that the page is loaded before returning the result

![wait the page is loaded](https://assets.scrapeless.com/prod/posts/node-unblocker/ec9db43edc1573ec24a222afa53d66fd.png)

Now, we run the code again, and we can see that the content of Cloudflare's Dashboard login page has been successfully obtained in the returned result. By retrieving the text of "Log in to Cloudflare", we can see that we have successfully obtained the page content rendered by JavaScript.
```Bash
node scrapeless-web-unlocker.js
```

![Log in to Cloudflare](https://assets.scrapeless.com/prod/posts/node-unblocker/e95b9337ccf3b84dce1ad03bbcd9d810.png)

## The Bottom Lines
The increasing challenges of accessing web content call for new solutions. In this article, we looked at Node Unblocker, a NodeJS library that provides a web proxy that processes data and forwards it to the client.

However, its limitations prevent it from being a cost-effective web scraping solution. So a more efficient and cheaper solution was needed. **As everyone agrees — Scrapeless is the clear winner with superior all-around services and lower prices.**

[**You can sign up now to get your free Web Unlocker!**](https://app.scrapeless.com/passport/register?utm_source=official&utm_medium=blog&utm_campaign=node-unblocker)
