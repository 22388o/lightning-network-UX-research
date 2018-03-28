# Objective three: review of current interfaces

The final section of this research will go through the current implementations of Lightning Network wallets with graphic user interfaces to point out the main good and bad design decisions that are being made. We have to consider, of course, that all the candidate clients for analysis are in a very early stage of development and are not actually functional yet. Due to that, there will be an effort to differentiate between what seems to be a design choice and what is a temporary implementation bug, since only the latter is relevant here.

Also, some of these wallets might have been created with demonstrative purposes only and, because of that, consciously didn't worry about details and usability issues. Even though, In order to make an equivalent analysys of all of them, they will be considered here

Also, some of these wallets might have been created with demonstrative purposes only and, because of that, consciously didn't worry about details and usability issues. Even though, they will all be considered here as wallets on the process of improvement, so any relevant issue will be pointed out so it can theoretically be corrected in the future.

Additionally, since the focus of the research is on usability and general user experience on the Lightning Network, aesthetics considerations will only be made when they directly affect those aspects \(e.g. cluttered interface that increases cognitive load, fonts that are too small to read, etc\).



Three different wallets \(in testnet mode\) will be used and compared with the guidelines defined in Objective two.

- HTLC.me \(https://htlc.me/\): a web wallet

- Zap \(https://zap.jackmallers.com/\): a desktop wallet

- Eclair \(https://play.google.com/store/apps/details?id=fr.acinq.eclair.wallet\): a mobile wallet



The scenario used to go through the wallets was the performance of simple expected operations \(sending and receiving payments\) and a basic exploration of the interface as a whole \(visiting and trying to understand the main available pages and sections\).

The first important observation is that some of the current implementations do not open channels automatically for the user, requiring them to search for the peer they need to connect to and manually open a channel. This wasn't even considered as an early development necessity in Objetive two because the required network structure for automatic opening of channels already exists as LND's autopilot feature. Although the network discovery methods will probably improve over time, the removal of the burden of opening channels manually can begin right now. The expectation is that, by the time functional releases for mainnet use are being distributed, this feature will have been implemented by the development team of all these interfaces.

Another general aspect of the current wallets is that, probebly due to the early development stage and the fact that they are only being used as testnet wallets, they didn't implement a proper set up for wallet security and backup. That's not a big issue if it's fixed before the wallet becomes usable in the mainnet.



HTLC.me

HTLC.me is a web based wallet created by Alex Bosworth with the basic necessities for the Lightning Network operation. Its greater strength is that it's very straightforward in its use and its greater issue is the lack of options and explanations for each activity. These aspects are a type of counterbalance and HTLC.me weights too much on the first side.

The first screen shows the amount available in a Bitcoin unit and in US dollar, as well as the three main sections of the wallet: send, receive and network. The wallet doesn't allow a blockchain funding operation, instead, it starts itself with the amount of 0.00016000 tBTC. This is probably due to the merely demonstrative purpose I mentioned before.

\(HTLC\_0\)

The first operation will be an emblamatic coffee purchase, using the Startblocks demo website \(https://starblocks.acinq.co/\#/\). As expected when purposing the wallet's sketches, the merchant provides both an easy way to copy or to scan the payment code. In the case of HTLC.me, only pasting or writing is possible, a scanning option would need to be implemented.

\(starblocks\_0\)

As soon as the payment code is pasted, the available information about the purchase is displayed. A perfectly timed feedback for the user before he confirms the payment.

\(HTLC\_2\)

After sending the payment, a confirmation screen with the transaction details is shown, which is also a proper feedback system. This concludes the first task of sending a payment.

\(HTLC\_4\)

The second step is to request a payment, which is made in the Receive tab by entering the desired amount you wish to receive. Here, an interlock is applied by only making the "Request Payment" button available after an amount is written down. This is a good application of an anti-affordance that tells the user that a payment request can only be generated with an amount. On the other hand, it might create a moment of confusion in case the user tries to understand how to generate the payment before writing anything in the amount field, because there' no available button. A better approach could be to display the button in an "off-mode", i.e., with a style that indicates that it's disabled \(such as a light/greyish color and no link behavior on hover\).

\(HTLC\_4\) \(HTLC\_5\)

After generating the payment, the payment code is displayed with the possibility of copying and visualizing as a QR code, as well as with a link that directly opens a wallet application on the device. A notification option is also provided for browser notification when the payment is received. The "reload" icon remains a mistery. If there was a title tag on the image, it could have given a better explanation of its function but, in this current setup, it's a button with no apparent effect when pressed.

\(HTLC\_6\) \(HTLC\_9\)

Here's the feedback when the payment is received:

\(HTLC\_10\) \(HTLC\_11\)

Note that no manual channel opening was required until now. That's because the HTLC.me already starts itself with a list of connected peers, as it can be seen in the Network section.

\(HTLC\_7\)

That's exactly what was mentioned before about removing the burden of opening channels of the user's shoulders, and HTLC.me does it quite well. What it apparently doesn't cover is the possibility of a user wanting to open a channel with a specific peer that doesn't appear on the directory.

The Network directory is also where the user's own peer address is shown, which is a place that makes contextual sense.



Zap



Zap is a desktop wallet developed by Jack Mallers and other contributors. Since it is a more complete interface, it naturally will have more elements to be analyzed and, possibly, criticized. It has, at its core, the intention of being user-friendly and the general aesthetic of the wallet is very pleasant. This last aspect is indeed important because users tend to perceive more pleasant interfaces as easier to use, so it's also part of a better usability.

Beggining with the first opening of the wallet, it presents a dark screen with an animated loading icon that counts a percentage of loading and a carroussel structure in the middle with a written content.

\(zap\_12\)

At the time of writing, the first experience with Zap already started with confusion for the user, because the loading process takes a long time and no explanation was given about what was loading. It looks like the user is stuck at this first page. This issue had already been pointed out in a Github issue and it appears that it is now resolved with the addition of a "Syncing to the blockchain..." message \(https://github.com/LN-Zap/zap-desktop/issues/243\).

Still on this same page, the carroussel can only be navigated by clicking the circles in the center of the page. Those circles convey the message of how many carroussel items there are and which one of them is activated. They do not, however, give the impression of being navigable links. The carroussel navegability should be improved by allowing direct control through keyboard arrows and adding some signifier on screen, such as left and right arrows, to better indicate where one should click to change items.

Also, although the explanation of Lightning Network is timely and clear, the other elements that are explained end up being so superficially described that not only fail to convey a useful knowledge but might even make users more confused. This moment the user has to wait for the syncing could be seized to give a more practical explanation about the wallet and its usage, accompanied by "learn more" links that will lead the interested person into a page with a proper explanation for these concepts.



\(zap\_1\)

When in the wallet, the beautiful interface will show an empty activity page. A mere suggestion here would be to include small explanations about each section while they are empty, so the user undestands what will go where at the same time that gets more information about how the Lightning Network works.

Since the wallet setup flow is not yet implemented, we're going to straight to the second flow from the Objective 2 section: making a payment. The PAY button is relatively easy to find, but is does have a usability problem that's worth mentioning.

\(zap\_0\)

The background color is a light yellow and the font used is white, thin and not very large. That's quite hard to read, even for someone with an OK vision. It's an accessibility issue that should be addressed somehow \(making the font larger, bolder, changing the font color to dark grey or changing the background color to a darker yellow\). The same is true for the REQUEST button.

The payment page is now open.

\(zap\_16\)

Again, we'll use the Starblocks page to make our purchase and get a payment code to paste in Zap.

\(zap\_14\)

It automatically completes with the amount of the payment and gives the feedback about the code being a valid Lightning Network payment. Although it is interesting that the page is very focused with the minimum of necessary elements, there are some extra information that could help the user, such as the previously suggested conversion of the amount to fiat currency \(in a smaller font\) and the possibility of adding a label to the transaction, in order to make it easier to find in the future when its listed with many others. After all, a great use case of the Lightning is exactly to make various small transactions, so it's likely that the list of past transactions will be very extense. Let's hit pay.

\(zap\_15\)

The transaction couldn't go through because there isn't a path to the peer we tried to pay. This means that Zap is one of the wallets which is being initially developed requiring users to open they own channels by hand every time they need. We aren't going to deeply analyze this process because this study's reccomentation is that this situation is reverted before the software is actually released for users on the mainnet. But we'll go quickly through the steps, since it will be necessary to complete the task of sending a payment.

\(zap\_18\)

That's the page for adding a new contact, i.e., opening a channel. As they might be useful when designing any other page of the wallet, some of the main perceived issues will be listed here:

- The contrast in the grey section is very low and one of the main elements of the page \(the submit button\) pratically disappears because of that and the small font size.

- The label "pubkey@host" could be more helpful if it displayed an example of the numeric format that is expected, such as "022f0edb0d6a8e19320e949a6f24fd4442c390ba1f38f8349b92ee0ee6cbdece08@35.229.31.135:9735". The visual cue of what the user is looking for is very important if he doesn't know exactly what he is looking for \(as he might not know what is a pubkey or a host\).

- The amount that is to be commited to a channel appears as a small detail on the bottom of the page \(it's shown after the "submit" button\) and it doesn't look very editable. It would be easy for someone to "add a contact" without even noticing that he had a choice there. This is mentioned in a Github issue: https://github.com/LN-Zap/zap-desktop/issues/272.

- Even for future wallets where the manual channel opening is less frequent, it would be useful to be able to add an alias or label to a new contact in order to make it more easily searchable and recognizible. This was also identified by other and put in a github issue: https://github.com/LN-Zap/zap-desktop/issues/227.

We finally have channels open:

\(zap\_3\)

This page of the interface has some very good elements, such as the searching option, a filter for contacts, a refresh option \(which could have a refresh icon next to it to call more attention\), and a clear state for each contact that is both written and color coded. As for the possible improvements: the already mentioned addition of an alias to each contact, the bad contrast in the "Add +" button \(same as in the PAY and REQUEST\). The division of the amount in the channel between "Can Pay" and "Can Receive" is an extra load on the user if he has to keep track of this for every transaction. But in the future case that this page is only eventually used for deliberate manual operations, it can add valuable information.

Now, if we repeat the steps of the payment flow, we will have a successful operation.

Our second task is to request a payment and, for that, we'll go into the REQUEST page.

\(zap\_17\)

Once you complete the request with the desired amount and label, you should receive a payment request such as this one:

\(zap\_8\)

It gives you a visible payment code, an option to copy and to scan, as well as displays the amount and the label you wrote in the previous step. Besides those basic elements, it also says the date the request was created and its current status \(if it was paid or not\). It really got all the elements right with the correct visual priority.

With that information, you can share the request with the person who is supposed to pay it and wait for a confirmation. Requesting a payment was also successful.

After a few transactions, here's what the wallet page will look like:

\(zap\_10\)

It perfectly represents the segmentation between Lightning and blockchain transactions, although the "Request BTC" and "Sent BTC" labels get quite repetitive. That space could be occupied by more informative label that will help the user identify them and the knowledge of what was requested or sent is conveyed through the positive or negative numbers in the right. It would be even clearer if the numbers were properly color coded as well and not only the differentiation for received transactions on the blockchain.

\(zap\_20\)

The doubt about that is the smaller number under the transaction amount is quickly answered by hovering the number and revealing that it is the transaction fee. The date of the transaction is informed, as well as if it's still pending \(represented by the clock icon that reveals an explanation when hoveren on\).

The biggest experienced issue is that unconfirmed blockchain transactions are not being shown, they only appear after confirmation. This is clearly a lack of proper feedback for the user that needs to know if the transaction is on its way but, as stated in the github issue about the subject \(https://github.com/LN-Zap/zap-desktop/issues/139\), it's probably a temporary bug.

A suggestion for the activity filter would be to create a segmentation in three main categories \(All, Lightning and Blockchain\) and use tabs instead of a drop-down, which has poorer discoverability. And, when in the Lightning tab, a submenu could appear with more refined options, such as sent, received, pending, invoices and complete. A different suggestion on the same theme was purposed on a Github issue, as well: https://github.com/LN-Zap/zap-desktop/issues/250.

With all the tasks completed, some extra comments about the interface are due:

\(zap\_13\)

Some messages displayed during the use of the wallet have a funny/playful tone that might not be appropriate to the situation. A wallet is a financial application, the users need clear messages and shouldn't be put in a playful mood because the operations they are performing might result in financial loss.

There is an issue that will be less frequent with an automated channel management, but an issue nonetheless. If you open multiple channels with the same peer, you have no warning or indication of that and the channels appear as completely different. That breaks the conceptual model of "contacts" that is passed on Zap \(you can't have two equal contacts that appear as different ones\). That is pointed out here on Github: https://github.com/LN-Zap/zap-desktop/issues/252. And the suggestion presented by this research is to either drop the "contact" analogy and call it a "channel" or to recognize repeated peers and group its channels under one name/pubkey.

\(zap\_17\)

Although not clearly visible at first, a repeated mistake during the wallet's operation has put to light a possible needed improvement. Both on the PAY and REQUEST sections, the label and payment code are requested as normal input fields, clearly recognizible but the user. Even though the amount is also an input field, it's shown in a completely different style \(very large and colored\), which passes, at first, as a decorative object. It looks very good aesthetically, but it might be more recognizible if it was in a more input-like style, similar to the other required element.

\(zap\_21\)

Taking a look at the "address" button from the wallet page, we can quickly see that the choice of a dark text color prevented it from having the same contrast issue as other buttons with a yellow background. Now let's take a look at where it takes us:

\(zap\_22\)

First, there is an inconsistent naming in which the blockchain address of the wallet is called "wallet address" in the QR code section and "deposit address" below. Also, this display is a bit confusing as it is, in practice, divided in "QR code section" and "written section". A more semantic division would be "deposit address section" and "node pub key section", each with a button to show the desired QR.

\(zap\_11\)

The Network section of the wallet is an interesting visualization model for the whole Lightning Network and it seems to be going in the right direction in terms of understanding the map and seeing peer information. It couldn't be explored very well during this study due to still unresolved development problems, but one observation can be made: is it really something to be in the same hierarchical importance as the "wallet" section? Specially when the auto-management of channels is implemented, this section shouldn't be so prominent as it has less practical use on daily user activities.

To finish the analysis over the Zap wallet, a few comments about the analogy system adopted by Zap that refers to channels as contacts. It is, indeed, a way to make users feel more familiar with the operation of the wallet as they use "add contact" features everyday in their lives. As for a "open channel" instruction, it requires immediate learning and might create resistance. But, sometimes, the lack of familiarity is necessary for the user to undestand that it is something new that he should be paying attention to. For example, the issue with the amount that is commited per channel being too subtle in the interface is exacerbated by the lack of need for it in the contact conceptual model. Why would someone need to choose an amount to add a contact to a contact list? The issue with the multiple channels opened with the same peer also brings confusion, but it could be solved by the appropriate grouping of channels.

In the proposed interface in Objective 2, the terms "add peer" were used, along with an explanation that you are opening a channel directly with a peer. The idea was to have a more understandable expression than "open channel", but with a lack of familiarity that will make the user pay more attention. However, that's really an issue that should be evaluated further. As it might be that this particular choice of words will end up with the worst effect of both sides \(not being technically correct and not being familiar\).

The moment of suggesting options and trying them out is really now, so Zap's choice is considerably good. And as there's no such thing as a perfect analogy, the main focus for future interfaces should be on maintaining consistency and standards among different ones. Other faulty analogies are used in Bitcoin systems everyday and is appears that users got used to them so far. But they are the same terms for every app \(address, coins, balance, etc.\). Requiring learning of new systems from users is far less problematic that it may sound if it only has to be done once.



Eclair
