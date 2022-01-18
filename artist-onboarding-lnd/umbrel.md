# Umbrel

## Overview

This guide will walk you through the steps required to connect your Umbrel/LND node to Wavlake. It requires a small degree of comfort with the command line and the ability to SSH into your node. We will provide code snippets where applicable to help make the process as easy as possible.

The steps below will help you identify your node's hostname, generate/download the correct tls.cert file, and generate/download a custom macaroon that will give Wavlake limited permissions to create and check invoices directly on your node. It may help to keep a notepad open while walking through this guide.

## 1. Hostname

In order to interact with your Umbrel, Wavlake needs a publicly accessible address to reach it. By default, Umbrel assigns the LND process an .onion hostname we can use for this purpose.

{% hint style="info" %}
The .onion address we are using here is not the same as the .onion address used to open channels with other nodes.
{% endhint %}

To retrieve this .onion hostname, navigate to the "Connect Wallet" section on the Umbrel homepage.

![](../.gitbook/assets/umbrel-connect.png)

Once there, open the drop down menu and select "lndconnect gRPC Tor" from the list.

![](../.gitbook/assets/umbrel-connect2.png)

On the page, you should see a URL with a long string that ends in ".onion". Copy the all the text in between "lndconnect://" and the "?" sign.

![](<../.gitbook/assets/umbrel-connect3 (1).png>)

&#x20;You should have something copied down that looks like:

> jfdsaoj930nglamljafafklajsdkfjdskafdsa9.onion:10009

This is your hostname (the .onion part) and port (the number part after the colon).

## 2. TLS Cert
