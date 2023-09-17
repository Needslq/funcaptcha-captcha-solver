# funcaptcha-captcha-solver


# How to Solve FunCaptcha with CapSolver

Welcome to another informative blog post from CapSolver, your trusted solution for handling all types of CAPTCHAs. Today, we'll be focusing on FunCaptcha, a unique and challenging type of CAPTCHA that's becoming increasingly popular across the web. We'll delve into what FunCaptcha is, the different types of FunCaptcha challenges, how you can solve them using CapSolver, and more.

## What is FunCaptcha?

FunCaptcha is an advanced CAPTCHA system designed to protect websites from spam and abuse. It replaces traditional text-based CAPTCHA systems with engaging mini-games that are difficult for bots to solve but easy and fun for humans. The main goal is to provide a user-friendly security measure that enhances user experience while maintaining robust protection against bots and spam.

FunCaptcha is powered by artificial intelligence to present challenges that are nearly impossible for bots to complete. This makes it a very effective and reliable tool for website security. As of the last update, FunCaptcha is utilized by thousands of websites worldwide due to its unique combination of user engagement and security.

## Types of FunCaptcha Challenges

FunCaptcha presents users with a variety of challenges, each designed to be easy for humans but challenging for bots. Here are a few common types:

1. **Image Rotation:** The user is presented with an image (usually an animal) that is out of alignment. The task is to rotate the image until it's upright. This task requires spatial awareness, a skill that bots generally lack.
2. **Object Identification:** The user must identify a specific object within a complex image. This tests the user's ability to understand context and detail, something that's currently difficult for artificial intelligence to replicate.
3. **Slide to Fit:** This challenge involves moving an object to its correct location within an image. This tests a user's ability to recognize patterns and shapes, another complex task for bots.
In this blog, we will focus on solving funcaptcha and looks like:
![How to solve FunCaptcha](https://assets.capsolver.com/prod/images/post/2023-05-16/acdc2ec9-d02f-4238-be48-2bd8b4c671e7.png)

## How to Solve FunCaptcha with CapSolver

CapSolver offers a reliable solution for solving FunCaptcha challenges quickly and accurately. Here's a step-by-step guide:

1. **Create an Account:** If you're new to CapSolver, the first step is to create an account. You can do this by visiting the CapSolver website and clicking on "Sign Up." Provide the required details and complete the sign-up process.
2. **Add Funds:** To use CapSolver, you'll need to add funds to your account. CapSolver offers a variety of payment options, including credit/debit cards and cryptocurrencies.
3. **API Setup:** Once you have funds in your account, you can set up the CapSolver API. The API documentation provided on the CapSolver website (docs.capsolver.com) will guide you through the process. It's straightforward and requires only basic technical knowledge.
4. **Send FunCaptcha Challenge:** Once the API is set up, you can send a FunCaptcha challenge to the CapSolver API. The API will return a response with the solution.
5. **Submit the Solution:** The final step is to submit the solution provided by CapSolver back to the website from which the FunCaptcha originated.

## Pricing

The pricing of FunCaptcha solutions via CapSolver depends on the volume of CAPTCHAs you need to solve. CapSolver uses a credit system, where each solved CAPTCHA costs a certain number of credits. For the most current pricing details, please refer to the CapSolver website.

## Why Choose CapSolver?

CapSolver offers a robust, reliable, and efficient solution for solving FunCaptcha and other CAPTCHA types. It's ideal for businesses and individuals who need to solve large volumes of CAPTCHAs quickly and accurately. CapSolver's API is easy to integrate, and the platform offers excellent customer support to ensure you can navigate any challenges with ease.

In conclusion, FunCaptcha is a unique and engaging CAPTCHA system, and with CapSolver, you can navigate these challenges with ease. Stay tuned to our blog for more updates and guides on solving different types of CAPTCHAs!




# How to solve FunCaptcha
Before we start solving FunCaptcha, there are some requeriments and points that we need to be aware that they are needed to know
**Requeriments:**
- **Capsolver Key**: This is an essential component in the process. Capsolver Key is a unique identifier that authenticates your requests to the CAPTCHA solving service.

- **Proxy**: While not strictly necessary, the use of a proxy is highly recommended when dealing with funcaptcha. A proxy server serves as an intermediary for requests from clients seeking resources from other servers, providing an additional layer of security and anonymity. For optimal results, you may consider using a reliable service such as MetaProxies.

While the proxy is optional, remember that funcaptcha places a high level of importance on the IP address. Therefore, using your own proxy is usually beneficial.

**Points to be aware that if we don't follow, solution will be invalid:**
In order to ensure the effectiveness of the solution, the following points must be meticulously adhered to. Failing to do so may result in an invalid solution:

- There might be an extra parameter that the Arkose Labs implementation might require. This parameter is used to transmit a `blob` value, which is an object that's been turned into a string. Here's an example of what this might appear like:
{"\blob":"INSERT_THE_blob_VALUE_HERE"}.

- **Recommended** of use your own `proxy`: The quality of the proxy you use can significantly impact the effectiveness of your solution. Poor quality proxies can lead to low scores.

For more details on solving funcaptcha, please refer to our [documentation](https://docs.capsolver.com/guide/captcha/FunCaptcha.html)

For this example, we will only use the required parameters. The task types for funcaptcha are:

- `FunCaptchaTask`: This task type requires your own proxies.
- `FunCaptchaTaskProxyLess` is using the server's built-in proxy.

We will use **FunCaptchaTaskProxyLess**. The example will be a  test page where there is funcaptcha. The page will be
For solve funcaptcha for the test site, we will just need to send to capsolver this information:

For get the captcha solved, first you need to submit all the information needed, for this we use the method `createTask`:
# Step 1: Submitting the information to capsolver
```http
POST https://api.capsolver.com/createTask

{
   "clientKey":"Your_API_KEY",
   "task":
        {
            "type":"FunCaptchaTaskProxyless",
            "websiteURL":"https://client-demo.arkoselabs.com/solo-animals",
            "websitePublicKey":"029EF0D3-41DE-03E1-6971-466539B47725",
            "funcaptchaApiJSSubdomain":"https://client-api.arkoselabs.com"
           
        }
        
}
```
# Step 2: Getting the results

To verify the results, you'll need to continuously poll the `getTaskResult` API endpoint until the captcha is resolved. 

Here's an example request:

```http
POST https://api.capsolver.com/getTaskResult
Host: api.capsolver.com
Content-Type: application/json

{
    "clientKey":"YOUR_API_KEY",
    "taskId": "TASKID_OF_CREATETASK" //ID created by the createTask method
}

```
Once the captcha is successfully resolved, you'll receive a response similar to the one depicted in the following image:
![](https://assets.capsolver.com/prod/images/post/2023-05-16/97a3bbe4-03b0-4e1c-9625-5066430940ea.png)



The captcha token received can be verified by submitting it to the relevant site. 
> ⚠️ **If the token is rejected, it may indicate that some information is missing or incorrect. We recommend thoroughly checking whether the FunCaptcha  whether requires additional parameters listed as optional in our documentation.**

In conclusion, while solving FunCaptcha may seem a daunting task, capsolver.com makes the process swift and efficient. By following the steps outlined above, you can easily resolve FunCaptcha.
     