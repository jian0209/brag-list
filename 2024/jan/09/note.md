# Sea Turtle Cyber Espionage Campaign Targets Dutch IT And Telecom Companies

[Reference from thehackernews](https://thehackernews.com/2024/01/sea-turtle-cyber-espionage-campaign.html?_m=3n%2e009a%2e3247%2ene0ao45e79%2e28qc)

- What is Sea Turtle?
  - A group of hackers aligned with the Turkish government.
  - New cyber espionage campaign understaken by a Türkiye-nexus threat actor.
  - Also known by the names Cosmic Wolf, Marbled Dust (formerly Silicon), Teal Kurma, and UNC1326.
  - Detailing state-sponsored attacks targeting public and private entities in the Middle East and North Africa.
- The infrastructure of the targets was susceptible to supply chain and island-hopping attacks.
- The attack group used to collect politically motivated information such as personal information on minority groups and potential political dissents.
- Primarily leveraging DNS hijacking to redirect prospective targets attempting to query a specific domain to an actor-controlled server capable of harvesting their credentials.
- Using SnappyTCP, the threat actor sent commands to the system to create a copy of an email archive created with the tool tar, in the public web directory of the website that was accessible from the internet.
- It is highly likely that the threat actor exfiltrated the email archive by downloading the file directly from the web directory.
- How to avoid?
  - Strong passwords
  - Multi-factor authentication (MFA) or two-factor authentication (2FA)
  - Rate limit login attempts
  - Monitor SSH traffic
  - Keep software up to date