# Raspiblitz

## Overview

**NOTE: This guide has not been thoroughly tested. Please make sure to back up any files you plan to change/edit and proceed with caution.**

This guide will walk you through the steps required to connect your Raspiblitz/MyNode/LND node to Wavlake.

The steps below will help you to 1) identify your LND's hostname and port, 2) generate/download a tls.cert file, and 3) generate/download a custom macaroon, all of which will give Wavlake limited permissions to create and check invoices directly on your node on your behalf. We advise keeping a notepad open on your computer while walking through this guide to keep track of the items you will need to register your server.

## 1. Hostname and Port

In order to interact with your node, Wavlake needs a publicly accessible address to reach it. You can use the mobile wallet connection feature to connect to Wavlake. Just use the "ZAP\_ANDROID" option as outlined in the [Raspiblitz docs](https://github.com/rootzoll/raspiblitz#mobile-mobile-wallet-apps-smartphone) to identify the hostname and port of your LND process. If you can't see the hostname and port in plain text, try running `sudo cat /mnt/hdd/tor/lndrpc/hostname` in your terminal.

In the end, you should have something that looks like this:

> jfdsaoj930nglamljafafklajsdkfjdskafdsa9.onion:10009

This is your LND's **hostname** (everything up to and including the .onion part) and **port** (the number part after the colon). Copy this information down.

NOTE: You will not need the colon ":" when entering your node details into Wavlake.&#x20;

## 2. TLS Cert

We now need to add the onion address identified in the last step to the LND conf so it can generate a new cert file for us with this hostname included in it.

Open the LND conf file by running `sudo nano /mnt/hdd/lnd/lnd.conf`. You should see a line in the file that says "tlsextradomain=" and a value. Add a new line below this with the new onion address we created in the last step. The line should look something like:\


```
tlsextradomain=jfdsaoj930nglamljafafklajsdkfjdskafdsa9.onion
```

There also is a script you can run on the Raspi to generate a new cert

`sudo /home/admin/config.scripts/lnd.newtlscert.sh`

If that does not work, you can restart LND with `sudo systemctl restart lnd`. This also should create a new cert file.\
\
Download the new cert.

## 3. Macaroon

The last item we need is a macaroon, which is a kind of key that allows you to perform specific actions on your LND instance. In order to give Wavlake only the minimum permissions needed to work with the site, we are going to custom "bake" a macaroon with those specific permissions only.

The simplest way to create a macaroon is by using the ThunderHub client. Find the "Tools" section in the left-hand navigation pane and click on it.

![](../.gitbook/assets/thub.png)

On the Tools page, you should see a "Bakery" section. Click on the "Bake" button and you will see a list of options appear.

Slide the following options to "Yes" (a visual guide is below): Create Invoices, Get Invoices, Get Wallet Info, Sign Messages, Verify Messages. Then click "Bake new macaroon".

![  ](../.gitbook/assets/thub2.png)

ThunderHub should display two versions of your newly baked macaroon. We want to use the "HEX" version. Copy the text for the HEX version of your macaroon and store it on your notepad.

## 4. Register

Now that we have all our items ready (hostname, cert, and macaroon) we can register our node with Wavlake.

Sign-up/sign-in to Wavlake and go to your Dashboard. If you have been approved to register with the site, you should see the "Add Server" button enabled. Click on it to open up the registration form.

![](../.gitbook/assets/dashboard01.png)

Fill out the registration form with the information you copied from your node and the tls.cert file you downloaded. The "server nickname" field can be whatever you like.

Once everything is filled out, press "Register".

![](../.gitbook/assets/dashboard02.png)

You should now see that the "Test Connection" button has been enabled on the page. Press it once to verify the connection to your node.

![](../.gitbook/assets/dashboard03.png)

Once the connection has been verified, the "Add Track" button should be enabled on your dashboard. You may now begin uploading tracks!

For more information about how plays and tips work, please see the [Mechanics](../mechanics.md) page.

If you ran into any issues along the way, send us a message at contact@wavlake.com and we will try and help you out the best we can.
