# Mechanics

The following is an overview of how Wavlake works, from its decentralized payment design to its playing and tipping mechanism.

## Architecture

![](<.gitbook/assets/Wavlake High-Level Design.png>)

Wavlake enables artists to receive Bitcoin payments over the Lightning network in exchange for their music. The diagram above gives an overview of how this works.

Every artist/label/music owner that registers a Lightning node with Wavlake grants the site the ability to create invoices on the owner's behalf. When a listener wants to make a payment to the artist, the site connects with the owner's node and creates an invoice. The site then shares that payment request with the listener and monitors the owner's node for when the payment has been received.

{% hint style="info" %}
Fees are collected automatically by the site by redirecting tips to Wavlake until the fee amount for the current period has been redeemed. After that payments are directed back to the artist until the next fee period.

NOTE: This feature will not be live during the testing phase of the site.
{% endhint %}

Upon receipt, Wavlake updates the tip total for the track and factors that into the track's overall ranking on the site (in addition to the track's play count).

## Plays

Wavlake is designed to give all visitors the ability to easily discover and listen to great music without necessarily having to pay with a Lightning wallet. At the same time, we want to give artists a fair trade in value for their work.

![](<.gitbook/assets/Wavlake plays.png>)

Every track starts with a number of free plays. This is set by the artist as high or low as they like (we recommend starting with 99). Once people start listening to the track on the site, the free plays tick down for each play that lasts more than 30 seconds. When the number of free plays for a track reaches 0, no one is able to listen to that track on the site anymore.

The way to unlock free plays is to send the artist a tip for it. Currently, the price per play is 100 sats (or about $0.04 at the time of this writing). So for every 100 sats a listener tips a track, it unlocks the corresponding number of free plays for both themselves and the public.

One way to think about this mechanism is to compare it to a jukebox, except on the internet. You put a coin in the jukebox, it plays a song for everyone in the bar. In the case of Wavlake, a listener's payment not only helps support the artist directly but also helps promote the track to other listeners because tips will push the track's ranking higher.

