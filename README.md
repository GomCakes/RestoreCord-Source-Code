# RestoreCord Source Code

> [!NOTE]  
> **New <ins>2024 source code</ins>:**
> The updated Next.js source code from March, 2024 can be [downloaded here (click)](https://github.com/restorecord-open-source/restorecord-new)
> <br>Instructions for self-hosting (cheaper/safer!) by `@million1156` Node.js are [here](2024-new-setup.md)

> [!WARNING]  
> **We recommend NOT using `restorecord.com`:** It's considered [a scam (proof)](https://imgur.com/a/uPFva8X) and constantly [banned from Discord](https://archive.is/hHth5), losing all member data.
> <br><br>After ownership changed in 2022 with Restorecord, it went downhill. And they [stole ownership](https://archive.is/s9SXR) with their history of [crypto draining fraud](https://i.imgur.com/wYtfumx.png)
> <br><br>The new ownership recently [sold personal data](https://nelsoncybersecurity.com/xenos-sell-data.mp4) revealed in a [data breach](https://archive.is/DhUUT) also covered in [global news with millions of views](https://www.youtube.com/watch?v=d0h4QPqAwss&t=1008s).
> <br>Owner and administrators also banned for [scamming (see)](https://imgur.com/a/uPFva8X), also the owner caught doing [credit card fraud](https://archive.is/v6E8B), and [token logging](https://nelsoncybersecurity.com/xenos-phishing-scumbag.mp4) and [password stealing malware](https://archive.is/qEN7k) and [tax fraud](https://archive.is/8ByAf).
> <br><br>I recommend using [VaultCord](https://vaultcord.com) with **<ins>4X more features</ins>** and also owned by the staff of [KeyAuth.cc](https://keyauth.cc) (very well-known service with 110K+ users). Far more trusthworthy than the "xenos1337" person of Restorecord [confirmed to be scamming](https://pub-d1677a93e4284baf8c2d931a541f3fd6.r2.dev/restorecord-2024-source-leak-data-breach-fraud-scams.mp4).

### Tutorial video how to host for 100% free forever: https://www.youtube.com/watch?v=804Fzc5j4vo

This is an old software project of mine spanning from April 2020 - January 2022. The code still works for current Discord API and functions as expected.

Written in PHP & C# - if you prefer a unified code project written in Next.js (Javascript), see the 2024 source code above.

## Copyright License

The code can be used for **commercial use** if you would like. No attribution needed 💯, though if you insist; it would be appreciated if you credited VaultCord.com ❤️

**<ins>NOTE:</ins>** nobody aside from myself (William Nelson) has legal rights to use my logo for RestoreCord [this one (not the new restorecord.com logo)](https://nelsoncybersecurity.com/rc-logo.png), or repost videos I've recorded for RestoreCord. If you do not follow this, you will recieve a copyright takedown.

**<ins>Don't worry</ins>** the logo isn't included in the source code, you would have to go out of your way to download the logo on another website, so you won't get a copyright takedown on accident 👍

## Features

- Multi server
- Restore members
- IP logging
- Discord webhook notifications
- Handles rate limits and access token refreshing. Most bots don't and break when you try to pull members, not this.
- VPN detection/block
- IP blacklist

## How to setup

PHP and MySQL. Should work on most PHP versions. I tested on PHP 7.4 and PHP 8.0, worked on both.
**You must have a VPS. Shared hosting such as NameCheap will not work, as you have to run c# application also**

Please setup your MySQL database now and import the structure from here https://github.com/wnelson03/RestoreCord-Source-Code/blob/main/restorecord_db_schema.sql

- Change the `restorecord.com` at https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L20 to `example.com` (where example.com) is your website's domain
- Replace `botTokenHere` with your Discord bot token https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L14
- (optional - only needed if you do NOT use cloudflare) change `HTTP_CF_CONNECTING_IP` to `REMOTE_ADDR` (do NOT do this if you're using cloudflare) at https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L77, https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L82, https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L120, https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L211, and https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L290
- (optional - only needed if you have more than 1,000 people verify a day) change `proxyCheckKeyHere` to a proxycheck API key if you have so many users you need to pay at https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L84
- Change OAuth2 authorization link at https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/verify/index.php#L419 you get your authorization link from Discord developer portal, like this https://imgur.com/a/G3q4oDM
- Change captcha keys here https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/register/index.php#L38 and https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/register/index.php#L101 or remove the captcha. I don't recommend removing captcha if you plan to sell this. Captcha is very neccesary for public websites. But if it's not a commercial site, you should remove lines 100-109 and then register will work
- Set MySQL connection info at https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L5
- If you have other users than yourself owning servers on this source and you want to log their actions, replace `discordWebhookHere` with your webhook url on https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/dashboard/account/settings/index.php#L445, https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/dashboard/account/settings/index.php#L499, https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/dashboard/server/settings/index.php#L573, and https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L23
- If you plan to sell this source, replace `8hCOmd6` with your Shoppy.GG product ID https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/dashboard/account/upgrade/index.php#L243 and then on Shoppy.GG, set these settings for the product https://imgur.com/a/XkRC3Pe and then make sure you set your Shoppy.GG webhook secret at https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L18
- Replace `DiscordBotClientID` with your Discord bot's application ID https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L12
- Replace `DiscordBotClientSecret` with your Discord bot's client secret https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L13
- Replace `https://restorecord.com/auth/` with `https://example.com/auth/` and use your website's domain instead of `example.com` https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L16
- Replace `https://restorecord.com/verify/` with `https://example.com/verify/` and use your website's domain instead of `example.com` https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/website%20source/includes/connection.php#L17

Now for c# part

- Change `https://restorecord.com/auth/` to `https://example.com/verify/` and use your website's domain instead of `example.com` https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/bot%20source/RestoreCord/Commands/Pull.cs#L113
- **(important, you don't want Discord to think you're a bot RestoreCord owns and ban you)** Change `RestoreCord (public release, 1.0.0.0)` to the name of your site or something https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/bot%20source/RestoreCord/Miscellaneous/Utilities.cs#L38
- Replace `rest_admin` with database username, replace `rest_main` with database name https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/bot%20source/RestoreCord/Services/Database.cs#L8
- Replace `databasePasswordHere` with database password https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/bot%20source/RestoreCord/Properties/Resources.resx#L127
- Replace `clientSecretHere` your Discord bot's client secret https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/bot%20source/RestoreCord/Properties/Resources.resx#L124
- Replace `discordIdHere` with your Discord bot's application ID https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/bot%20source/RestoreCord/Properties/Resources.resx#L121
- Replace `botTokenHere` with your Discord bot's token https://github.com/wnelson03/RestoreCord-Source-Code/blob/eef52c3e87ff59b0b928f58cf8332dfde4060543/bot%20source/RestoreCord/Properties/Resources.resx#L139

Written for Debian 11

```bash
wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
```

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0 dotnet-runtime-5.0
```

For this next part make sure you are in the bot's root directory.

```bash
dotnet restore
dotnet build
```

You now have an executable!

Create a service using systemctl, make sure to replace the paths.

```
[Unit]
Description=Restorecord
After=multi-user.target
[Service]
WorkingDirectory=/path/to/working/directory
ExecStart=/path/to/bot/executable 
SyslogIdentifier=Restorecord
Type=idle
Restart=always
RestartSec=15
RestartPreventExitStatus=0
[Install]
WantedBy=multi-user.target
```

Once you set this up, the bot should come online and slash commands should work, do `/` and you'll see slash commands

Here's a YouTube video showing how to use the bot https://nelsoncybersecurity.com/restorecord-tutorial.mp4


**How to give yourself lifetime premium (replace `yourUsernameHere` with your username):**
```sql
UPDATE `users` SET `role` = 'premium',`expiry` = 2224663363 WHERE `username` = 'yourUsernameHere'
```
