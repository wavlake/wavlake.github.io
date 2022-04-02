# Mechanics

The following is an overview of how Wavlake works, from its decentralized payment design to its playing and tipping mechanism.

## Architecture

![](<.gitbook/assets/Wavlake High-Level Design.png>)

Wavlake enables artists to receive Bitcoin payments over the Lightning network in exchange for their music. The diagram above gives an overview of how this works.

Every artist/label/music owner that registers a Lightning node with Wavlake grants the site the ability to create invoices on the owner's behalf. When a listener wants to make a payment to the artist, the site connects with the owner's node and creates an invoice. The site then shares that payment request with the listener and monitors the owner's node for when the payment has been received.

Upon receipt, Wavlake updates the tip total for the track and factors that into the track's overall ranking on the site (in addition to the track's play count).

## Plays

Wavlake is designed to give all visitors the ability to easily discover and listen to great music without necessarily having to pay with a Lightning wallet. At the same time, we want to give artists a fair trade in value for their work.

![](<.gitbook/assets/Wavlake plays.png>)

Every track starts with a number of free plays. This is set by the artist as high or low as they like (we recommend starting with 99). Once people start listening to the track on the site, the free plays tick down for each play that lasts more than 30 seconds. When the number of free plays for a track reaches 0, no one is able to listen to that track on the site anymore.

The way to unlock free plays is to send the artist a tip for it. Currently, the price per play is 21 sats (or about $0.01 at the time of this writing). So for every 21 sats a listener tips a track, it unlocks the corresponding number of free plays for both themselves and the public.

One way to think about this mechanism is to compare it to a jukebox, except on the internet. You put a coin in the jukebox, it plays a song for everyone in the bar. In the case of Wavlake, a listener's payment not only helps support the artist directly but also helps promote the track to other listeners because tips will push the track's ranking higher.

The "Power" bar for each track gives an indication of how many free plays remain for the track. When the bar is empty, all the free plays have been used and someone must tip the track in order to unlock it again.

## Fees

Wavlake takes **no fees** on any tips _if you have connected your own node_ to the site.

For artists/labels using the [Lightning address](https://lightningaddress.com) feature, the site will collect 1 sat for every 21 sats tipped by users. This comes out to approximately a **4.7% fee**. The fee helps 1) cover forwarding costs for tips and 2) contribute to maintenance of the site.
