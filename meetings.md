# PLN Data-Compliance WG

## Basic Info

- Primary mode of communications: #wg-data-compliance on [Filecoin Public Slack]()
    - async longform collab?
    - Slack versus Github Discussions?
- Meeting cadence: monthly meetings for now?
- IPR regime: ?
- Confidentiality: opt-in for specific work items as needed but maximally transparent by default as per [PLN norms](https://protocol.ai/blog/announcing-the-permissive-license-stack/)
- Steward/Responsible Idiot: Juan Caballero, aka [bumblefudge](https://github.com/bumblefudge) on Filecoin Public Slack

## Meeting Notes

### Kickoff - 5 Feb 2023, 8am PST / 5pm CEST
- Agenda
    - QUICK intros [1min per co, 1min per individual]
    - Decide short-term goals and, ideally one deliverable (or more) for Q1/Q2
    - Update Basic Info above
- Intros
    - Juan: lots of experience w/personal data; no agenda, no dayjob (just love PLN)
    - Boris: long experience; founder of Fission, which needs a ToS and GDPR compliance on our backlog since forever
        - Fission in a nutshell: we give users a personal file system, so we want to imagine 
    - Marjorie: Head of legal for Fractal.id, based in Porto; Fractal is a KYC/DID provider with web3 use-cases; span custodial and non-custodial/exportable storage of personal data
    - Robin: Work for Protocol Labs, on standards and governance; before that worked on NYT for 5 years on privacy, GDPR and related issues
    - Addie: Network Goods team; archaelogical association (hypercerts, impact evaluation, other onchain opensource/funding mechanisms); worked on various L1s and FOSS before this
    - Martin (identity.com): Solana onchain DIDs; Filcoin 
        - have worked on many projects that get "shut down by GDPR" - might be easier to solve on network 
    - Daniel (Civic): we build apps on identity.com stuff; we issue VCs to KYC'd users that go in their wallets 
- Goals and deliverables
    - Boris: mission statements and scope?
        - GDPR compliance
            - mental models for "deletion"?
            - public/private network
    - Boris: permissioned data WG in Lisbon - Addie 
        - WinFS - DIDs + Caps --> Permissioned data (implementation direction)
        - funding unclear atm, tho, or else already would be a WG
    - Boris: IPFS Operators WG
        - bad bytes list experience - hard to figure out geolocating regulatory obligations without "censoring at protocol level" - need to do both at both levels
        - Robin: DSA going into force will make this more relevant - takedown framework
            - DMCA = just copyright; DSA = broader, content-based criteria, malware, phishing, etc
            - 230 analogue (includes safe harbor clause, like 230)
            - applies differently 
            - very web2 definitions/concepts of "deletion", "publication," etc
    - Martin: I want to learn from decentralized storage veterans; my impression is that filecoin core/foundation, PLN core/foundation, and Arweave core/foundation could (and maybe should?) take leadership here, I'm curious what they think/want
        - Boris: I don't think they have a uniform/official position here, they want to stick to lower (protocol) layer(s) and consider compliance an app-level problem; 
        - Boris: IPFS does not want policy built in at that layer (//S3)
            - Anecdote: NFTs coalescing on IPFS-flavored CIDs, which de facto pumps traffic through IPFS https gateway; we got takedown requests from CIDs that looked like fission-generated/-hosted content because we controled a domain serving other gateways' CIDs
            - Anecdote: Open relaying --> lots of DNS whackamole
        - Martin: VCs or attestations/reputation for nodes? Boris: That's a diff layer/problem tho
        - Boris: Bad bytes list might be a good federation-layer for agreeing to mutually-enforce shared policies
        - Martin: How compose?
    - Daniel: I'd love to have a mental model for layers and on which layers compliance building blocks live
        - Boris: As long as we don't decide ONE REGULATORY LAYER
    - Robin: Privacy threat model for IPFS
        - ex.: How data leaks? How do encryption keys leak and what happens if they do?
        - ex.: How do GDPR and CCPA differ in defining PII/toxic data?
        - Operators aren't only actors here-- 
            - ex. running an IPFS node in a browser or on edge device? Doesn't the CIDs you're propagating thumbprint the node? (YES PROBABLY)
        - Boris: FAQ/wiki-collaboration model
    - Martin: Chip away at the perception of a fundamental **Irreconcilability** of Private data and Public networks
        - threat model could be a discouraging starting point, just maps out the problem space; we should publish a conditional path forward!
        - Robin: Yes, we are breaking into pieces the work of putting forth a legal theory!
        - Boris: MANY protocol and protocol+app projects I could name are waiting and hoping for this precedent/legal theory!
    - Marjorie: I agree; one of my main painpoints when I started researching IPFS because I didn't understand it or its privacy attack vectors/architectural division of labor, so let's defo start there
        - layering IPFS with other GDPR-conscious protocols and architecture...
        - Geo-fenced nodes? That would also help our design efforts
    - Robin: Industry-specific problems and innovative 
        - good CoC articles from EU: Cloud Hosting has one
        - Boris: Code of Conduct for IPFS operators would be great!
            - Cloudflare would likely be interested, given their history
    - Boris: Do we have a good technical definiction and/or regulatory best practices for "Tombstoning"?
- Next steps
    - Boris: i'd love to know which laws I should be worried about
    - GH Discussions will be where most magic happens
        - intro yourself as soon as there's a place for doing so!

## Bibliography

Feel free to add to this! Anything you think might be helpful for research, meetings, etc.

Primary Documents
- [Text of DMA](https://eur-lex.europa.eu/legal-content/en/TXT/?uri=COM%3A2020%3A842%3AFIN) (and official translations)
- [Text of GDPR](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A31995L0046)
    -[2016/679 (replaced 95/46/EC)](https://eur-lex.europa.eu/eli/reg/2016/679/oj)
- [Text of DSA](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A32022R2065)

Guidance
- [EU Code of Conduct guidance for Cloud Hosting](https://scope-europe.eu/en/projects/eu-cloud-code-of-conduct/)
- CSAM regs for bad bytes?

Useful Secondary Sources
