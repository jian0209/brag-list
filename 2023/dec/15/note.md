# The Value Of Repaying Good Technical Debts

[Reference from TLDR](https://www.infoq.com/news/2023/12/repaying-good-technical-debt/?utm_source=tldrwebdev)

- Bad technical debt is the stuff has been lingering around.
- The only attention it gets from the team is working around it, or fixing the fallout as a consequence of this bad technical debt.
  - limit team, and as a consequence, the team members feel hopeless.
- Type to know the good technical debt
  - It is intentional
    - The technical debt is not just there because it happened to us, but because we made a conscious choice to take a shortcut.
  - It enables
    - The organisation benefits from taking on the debt initially because it allows us to generate more value.
  - IT is controlled
    - Eg: Tripwires that inform us when we are nearing the point where the interest we pay exceeds the value that we gained.

# Name Checker(Tool)

[Reference from TLDR](https://tracking.tldrnewsletter.com/CL0/https:%2F%2Fnamechecker.vercel.app%2F%3Futm_source=tldrwebdev/1/0100018c6319c07a-d056303b-765a-47ed-82a1-2ee21864e38d-000000/kN0OMg7mwlDYdl9dZnboT70A7TTyw8w-CRO3ydl_mME=331)

### This is a tool to check is the name is available on github, npm, etc, and also check the domain name availablity.

# How To Analyze Malware's Network Traffic In A Sandbox

[Reference from TheHackerNews](https://thehackernews.com/2023/12/how-to-analyze-malwares-network-traffic.html?_m=3n%2e009a%2e3225%2ene0ao45e79%2e27us)

- Decrypting HTTPS traffic
  - Hypertext Transfer Protocol Secure(HTTPS), the protocal for secure online communication, has become a tool to defend the malware for their malicious activities.
  - By cloaking data exchange between infected devices and command-and-control (C&C) servers, malware can operate undetected, exfiltrating sensitive data, installing additional payloads, and receiving instructions from the operators.
  - To decypt HTTPS traffic is the easy task, can use a man-in-the-middle(MITM) proxy for this purpose.
  - So how the MITM proxy works, is an intermediary between the client and server, intercepting the traffic and decrypting it before forwarding it to the destination.
- Typical stealer can gains access to passwords storeed in browsers, and transfer them to the attacker's server.
- Discovering malware's family
  - Malware family identification is a crucial part of any cyber investigation.
  - FakeNET offers a solution to this challenge by creating a fake server connection that responds to malware requests.
- Catching geo-targeted and evasive malware
  - Incorporate mechanisms like IP geolocation, language detection, or website blocking which may limit analysts' ability to detect them.