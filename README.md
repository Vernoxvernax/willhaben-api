# Willhaben - API Documentation

This is a WIP documentation for the API powering the second-hand market place [Willhaben](https://de.wikipedia.org/wiki/Willhaben).

For information on how to create an application token, which is required for almost every request, see [applicationToken.md](applicationToken.md)

___


**Feel free to create issues and or pull requests.**

___

### **How:**

Since the web version of willhaben only provides static text, we get the api specs through the mobile apps.

Because of the use of SSL-Pinning, [mitmproxy](https://mitmproxy.org/) alone, isn't enough to monitor the network traffic.
If you want to help me document the rest of the endpoints or potential future changes in the API, I recommend the following tools (android):
* [mitmproxy](https://mitmproxy.org/) to monitor the network requests
* [jadx](https://github.com/skylot/jadx) to unpack the apk
* [frida](https://github.com/frida/frida) for ssl-unpinning code-injection
  * [frida_multiple_unpinning.js](https://gist.github.com/akabe1/5632cbc1cd49f0237cbd0a93bc8e4452). This is one of the very few unpinning scripts that actually work. [Httptoolkit](https://github.com/httptoolkit/httptoolkit) also works if your phone is rooted and you don't have a problem with light mode GUIs (not-recommended).

#### **Android phones without root**:

+ no idea, I have a rooted phone, sorry. But it's possible

___

See [**Redocly/openapi-starter**](https://github.com/Redocly/openapi-starter) for more information about to build the documentation with redocly.
