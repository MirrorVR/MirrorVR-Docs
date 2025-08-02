# Meta Quest Setup

{% hint style="warning" %}
Before starting this, you must have done basic setup. See [.](./ "mention") for basic setup.
{% endhint %}

Meta Quest is one of the most used platforms for VR, so there's no doubt that you'll probably want to add support for it. So, here's a guide on how to add Meta Quest Support to your MirrorVR game!

{% stepper %}
{% step %}
First things first, go to the [Oculus Developer Dashboard](https://developer.oculus.com/manage/), make an organization if you haven't, and then make a new app with the platform as "Meta Horizon Store". \
\
If you didn't have an organization before, you will need to verify your identity before you can publish. If you are just a normal person, no business records, just go with admin verification. If you do have business documents related to your organization, then you can do business verification.&#x20;

{% hint style="info" %}
Your legal name in the [Meta Accounts Center](https://accountscenter.meta.com/accounts) MUST match the name on the ID if doing admin verification.
{% endhint %}

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
Let's hold on the Meta Dashboard for a second. Go back to your Unity Project.\
Install the [Meta XR Core SDK](https://assetstore.unity.com/packages/tools/integration/meta-xr-core-sdk-269169) and the [Meta XR Platform SDK](https://assetstore.unity.com/packages/tools/integration/meta-xr-platform-sdk-262366) into your project.

Once done, go to your project again and at the top, click on `Meta > Platform >` \
`Edit Settings`.&#x20;

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
Let's add your App IDs. Go back to your Meta app in your browser. On the left-hand sidebar, go under `Development > API`.&#x20;

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Here is where all of your App IDs are. Go down to the App ID header, copy your app ID, and paste it in both the Oculus Rift and Meta Quest App ID fields on the settings. \
\
Make sure you also enable the `Use Standalone Platform` and `Use Meta Quest App ID over Rift App ID` boxes.

{% hint style="danger" %}
**DO NOT** share these IDs with **ANYONE**! The App Secret **alone** can give hackers access to many things you wouldn't want.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Note that App IDs and Federated App IDs are two different things! Make sure you use the _App ID,_ not the _Federated App ID_!
{% endhint %}


{% endstep %}

{% step %}
Now your Platform Settings should look something like this:

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Now the big error box, how do we fix that you may ask. Easy! Go back to your browser, and on the left-hand sidebar, go to the tab just below API, which should be called "Test Users".

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Then go to the top right and hit the `Add Test User` button.\
Go ahead and fill out all details.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Then hit submit at the bottom right and wait a bit.


{% endstep %}

{% step %}
Now after waiting, it should have created a test user. Go to the three dots on the right of all the details, and hit `View Test User Data`.&#x20;

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Now hit the Copy button next to the email email field, then hit cancel. Go back to Unity, and paste the email you just copied into the `Test User Email` field, and type in the password for the test user in the `Test User Password` field. Then hit login.\
\
If your Unity Editor Settings looks like this, then you're all set!

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
Open back up the API tab for later, we will need those in the Epic Portal. The duplicate that tab, and go all the way down to the `Requirements` section, then click on `Data Use Checkup`.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

At the top of the DUC page, it will most likely have a banner saying `Self-certification is incomplete. Action is required.` Hit the start button to the right.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Select `Teens and Adults`, then hit continue, then confirm.

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
If you select any others, Meta will limit your app and make you add the Age Group API, which is NOT fun to set up.
{% endhint %}


{% endstep %}

{% step %}
Now onto the Data Use Checkup. We have two we need to add, User ID and User Profile.\
To the right of the User ID field, select `Add`.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

In usage, click on the dropdown and select `Use Peer-to-Peer (P2P) Networking`.\
In the description, say something like "We are using User ID for authentication with Epic Games to use their free relay service."\
\
Check the box at the bottom that you agree, and hit `Add to request`.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Do the same thing with User Profile. Usage as `Use Peer-to-Peer (P2P) Networking`, description something along the lines of "We are using User Profile for authentication with Epic Games to use their free relay service.", check the agree box, hit Add to request.


{% endstep %}

{% step %}
Now onto the most complicated part, submitting the request. Meta uses so much legal language that we are going to dumb it down for you to make you have less of a headache.

Firstly, at the top, hit `Submit requests (2)`. Now a big window pops up.\
As of August 2025 (any of this is subject to change by Meta, so it may not be the same for you), this is what all of it says:

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

This one is asking if you have any databases/player management services that hold Meta Quest User Data. Most likely, if you are following this tutorial, you do. If you do have any, select yes, if not, select no.\
\
If you selected no, you can skip to the next question. If you selected yes, follow this next question.

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

This one is pretty straight forward,  hit Add data processer or service provider.\
For each provider you use, click the button once. I'm going to add one for Epic Online Services, but if you use PlayFab you have to add that in as well.\


<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Again, straight forward, just put in whoever controls the data, such as Epic Online Services or PlayFab.

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Easy enough, whoever controls your data, search up "(company name, such as EOS) headquarters". Whatever country their HQ is in, put that here.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

This question is basically if law enforcement has requested any Meta Quest User Data. Most likely not, but you know your game best, so answer honestly.

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

This is basically what you would do if law enforcement requests any user data. If you don't know any of the options terms, just select None of the above.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

And our last question. Easy enough, just select the country where you live.


{% endstep %}

{% step %}
Once done with all those questions, select Next at the bottom right, Next again, then check the agree box and hit Submit for Review. Now wait 1-4 business days. If you're doing this on the weekend, Meta employees have the weekend off, so you most likely won't hear back before Monday.&#x20;

{% hint style="info" %}
While you're waiting , you're good to do the next step!
{% endhint %}


{% endstep %}

{% step %}
The next step is to go to your app on the [Epic Games Developer Portal](https://dev.epicgames.com/portal), then go to Product Settings.

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Then go to Identity Providers.

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Hit `Add Identity Provider`.

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
On the Identity Provider dropdown, select Oculus.\
Set Description to your game name, and Environment to Quest. Remember that APIs tab from earlier? Go back to it. Copy your App ID and App Secret and put it in the slots.

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**DO NOT** share these IDs with **ANYONE**! The App Secret **alone** can give hackers access to many things you wouldn't want.
{% endhint %}

Once you're done, hit `Save & Exit` at the bottom right.


{% endstep %}

{% step %}
Now that you have the identity provider set up, go to the sandboxes tab.

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Then on the `Live` sandbox, hit `Identity Providers`.&#x20;

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Go down to Oculus, and select the IP you just made.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

Hit the X in the top right, and you're all set! You fully completed setup.
{% endstep %}
{% endstepper %}
