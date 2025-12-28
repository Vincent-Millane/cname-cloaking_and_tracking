# DNS blocking lists, Pihole, Unbound for cname-cloacking, trackers or intrusive advertising.

**Table of Contents**  

  - [Why ?](#why-)
  - [Unbound for Linux, Mac and Windows](#unbound-for-linux-mac-and-windows)
  - [Pihole for Linux, Mac and Windows](#pihole-for-linux-mac-and-windows)
    - [Tips](#tips)
  - [About aggressive trackers](#about-aggressive-trackers)
    - [mobile.pipe.aria.microsoft.com](#mobilepipeariamicrosoftcom)
    - [mobileconfig.sascdn.com](#mobileconfigsascdncom)
    - [fundingchoicesmessages.google.com](#fundingchoicesmessages.google.com)
    - [The Malwarebytes case](#The Malwarebytes case))
  - [Extensions for Android and IOS devices](#extensions-for-android-and-ios-devices)
    - [Blocking trackers and intrusive advertising](#blocking-trackers-and-intrusive-advertising)
    - [Fingerprinting the web](#fingerprinting-the-web)
  - [Adguard for Android TV, Linux, Mac, Windows](#adguard-for-android-tv-linux-mac-windows)
  - [License](#license)


## Why ?

Cname-cloacking is in breach of European law (GDPR) and the law in many countries (California and Australia seem well inspired too) because they hide the DNS references of the site you are visiting. It is therefore impossible to obtain user consent for these third-party sites and the immediate effect is that you are tracked on all sorts of sites.

This is a more pernicious method than third-party cookies because it is tacit and there is no recourse. It's a real goldmine for the companies that use it.
It's staggering when you consider that some of these companies boast that they can be connected to 600 other trackers.

They can keep your data for as long as they like, since it does not officially exist. This can mean your whole life, as we have seen with databases revealed that have 2 or 3 times the number of people on earth.

Would you like to have a spy on your shoulder from morning to night, analysing your every move throughout the day, right down to the brand of toilet paper you use?

A recent revelation showed that certain viruses could hide in the advertisements of a major global company using information that was not available to the public. This is nothing new, but now it's been proven.

The issue of energy savings and the autonomy of our connected devices is now very important. It's a question of ecological common sense. 
Premature ageing due to over-solicitation of advertising is a major factor. The image of a vehicle in overdrive dragging advertising hoardings seems appropriate to me.



## Unbound for Linux, Mac and Windows

You can install the excellent DNS software that also caches [DNS unbound:](https://www.nlnetlabs.nl/projects/unbound/about/ "Unbound is a validating, recursive, caching DNS resolver")
You can then include the stub-zone list [stub-zone](https://github.com/Vincent-Millane/cname-cloaking/blob/main/stub-zone "Stub-zone list for Unbound").


## Pihole for Linux, Mac and Windows

For a family or with the multitude of connected objects, installing [Pi-hole is **very effective**:](https://pi-hole.net "A black hole for Internet advertisements")

These solutions offer huge savings in data and bandwidth, not to mention considerable energy savings.

For example, Pihole blocks 35-60% of advertising and trackers. This translates into a 50% increase in battery life for my Samsung smartphone.

I have created blocking lists for Pi-hole. You can download them to your computer and open them with your favourite editor.

* A list based on strict regexes of domain names [pihole_domains_list.txt](https://github.com/Vincent-Millane/cname-cloaking/blob/main/pihole_domains_list.txt "List of regexes for Pihole domains")
* A list based on regexes that take sub-domains into account [pihole sub-domain list.txt](https://github.com/Vincent-Millane/cname-cloaking/blob/main/pihole%20sub-domain%20list.txt "List of regexes for Pihole subdomains")

Do not add these lists as text lists because the regexes will probably be treated as text.

The solution, which only takes a few seconds, is to copy each list and paste it into the pihole graphical interface for adding regexes in :

_Domains > Domain management > RegEx filter_
and paste into the field.

Clicking on the _‘Add to denied domains’_ button will add the regexes to Gravity's sqlite3 database in a few seconds.   
You will notice that the red icon to the right of "Domains" has increased accordingly.

Pihole remains the ideal solution for protecting **all the devices in your home** as soon as you can specify a DNS server on your private network. 

Pihole even protects you outside your home if you use a VPN that connects you to your web router.

### Tips

- In my observations, I have found that it is risky to use Android applications that have hard-coded calls to trackers, bugs and advertising agencies. I assume the same applies to iPhones, but I don't have any to verify this.  
As far as possible, use a good browser with extensions that protect your privacy (high marks to [cookie-autodelete](https://github.com/Cookie-AutoDelete/Cookie-AutoDelete "Cookie-Autodelete extension for Chrome, Mozilla, Edge") for taking care of cookies). This will be enough to block all these malicious trackers, although there are a few caveats.

- It is possible that the regexes can block sub-domains of sites that you like with Pihole, the solution is to set the blocked line to ‘Allow’ to authorise this sub-domain or to go faster, you can type the following in a console:  
`sudo pihole --allow-regex '(\.|^)subdomain\.domain\.com$'`

- About my methodology, I use the same one as firewall administrators use on a computer network. 
I block anything suspicious, then gradually allow what needs to be allowed to create tailor-made exceptions to the rule.  
You can create exceptions with the “Allow” button in Pihole's query logs item.
Bear in mind that a viral load can be sent via a zero-click ad.

## About aggressive trackers ##

### mobile.pipe.aria.microsoft.com ###
If you're experiencing several thousand connection attempts a day to **mobile.pipe.aria.microsoft.com**, which are draining the resources of your installation as well as those of your smartphone, you can stop and then disable the **Link to Windows** application on Android. 
> [!NOTE]
> On Android 15, go to  
_Settings > Applications_   
and search for the **Link to Windows** application.   
This stops all connections immediately.   
If you need this app for any interaction with Windows, you can activate it for as long as you need, and deactivate it when you're done. 
This application contains trackers that do not justify the tsunami of connections. 


### mobileconfig.sascdn.com ###
If you have hundreds of connections per day (more than doubleclick!) to **mobileconfig.sascdn.com**, it's also an aggressive tracker that's linked to the Smart AdServer tracker, which in turn is linked to Akamai (akamai.smartadserver.com). 
These domains are included in my list of domains. 

A search in the trackers tab of the excellent [Exodus application](https://exodus-privacy.eu.org/ "εxodus - the Privacy Auditing Platform for Android Applications") will show you all the applications containing this bug at the date of their last scan. It is possible to request an online scan of an application. 

To put an end to this energy-hungry drain on your smartphone's resources, all you have to do is stop each of the offending applications in turn.   
> [!NOTE]
> On Android, just go to  
__Settings > Applications_   
to stop the flow of connections immediately. 
You are free to deactivate or not the application in question, depending on your usage.
In my case, it was an application from an institutional weather service in my country.

### fundingchoicesmessages.google.com ###

With 9,940 connection attempts per 24 hours, I agree with those who believe that these connections are associated with tracking devices. I don't surf the internet enough to consent to so many cookie permissions. 
The excessive number reveals an automated system that is independent of our internet activity and has a purpose that is very different from the stated goal.
> [!NOTE]
> It would appear that news aggregators are powerful conveyors of these connections. 


### The Malwarebytes case ###
There is no denying that this once excellent anti-malware program has slipped into a somewhat shady area. 
There was a time when launching this security application connected to two crash tracking trackers (apparently), but now it connects to more than half a dozen well-known trackers. This is highly suspicious, especially for an application that is supposed to protect our data, not sell it to a nebulous network of interconnected trackers around the world. 
Unfortunately, these hidden trackers cast a shadow over the meticulous work of the company's researchers. 
To keep this application, it is best to stop it after a scan to avoid thousands of malicious connections. 
I uninstalled it because it is untrustworthy, with the specter of venal bias during a scan or a flaw related to the trackers' APIs.
> [!IMPORTANT]
> Security applications do not have any trackers. This is how they remain credible.

## Extensions for Android and IOS devices 

### Blocking trackers and intrusive advertising

Starting with the excellent [ublock origin](https://ublockorigin.com "Free, open-source ad content blocker").

I found a cool [Privacy Badger extension](http://privacybadger.org "free browser extension made by the leading digital rights nonprofit EFF") that doesn't block ads but all cnames and other vicious trackers.

To block advertising Adguard is stable.
In the advanced settings, there is a watchdog option to restart Adguard. 
This is very useful if you find that Android regularly disables Adguard. It's an admission that this software is powerful.

The Adguard browser extension has a number of advantages [Adguard works on Android and IOS](https://adguard.com/fr/welcome.html "AdGuard Ad Blocker").

### Fingerprinting the web

With Librewolf, it is becoming commonplace to find that more and more websites are taking a fingerprint of your browser (in anticipation of the blocking of third-party cookies that is becoming more and more common?)
This is obvious when using Librewolf, which has an activated option

Firefox does not activate it by default, which can be checked on the `about:config` options page where the **privacy.resistFingerprinting** item is set to false, as are others.

To protect against fingerprinting and avoid being tracked from site to site and tracker to tracker, there is the [CanvasBlocker extension](https://github.com/kkapsner/CanvasBlocker "This add-on allows users to prevent websites from using some Javascript APIs to fingerprint them"). This extension is available for the Mozilla family and all Chromes.  
Simply install it with the default settings. By pinning it to the toolbar, you can see the icon change from green to red, indicating the number of fingerprints blocked.


## Adguard for Android TV, Linux, Mac, Windows

Adguard exists as software that protects Android computers and televisions from [ads, trackers and phishing](https://adguard.com "AdGuard browser extensions are among the fastest and most lightweight adblock extension").

\
\
\
If you wish to value my work and my investment, you can do so in Monero crypto-currency with this account number:

> 8AwD8HWyj1KSePrnk3VmkLJf3QQYKCHKmHBCZw4YBqEsLQpApAYUjRzQFx8WEQQqz78QXptAJvHQMPB2vp94pxiZTwtput9

I appreciate it.


## License


 <a href="https://github.com/Vincent-Millane/cname-cloaking_and_tracking">cname-cloaking_and_tracking</a> © 2022 by <a href="https://creativecommons.org">Vincent Millane</a> is licensed under <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a><img src="https://mirrors.creativecommons.org/presskit/icons/cc.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/by.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/sa.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;">

