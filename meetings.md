# PLN Data-Compliance WG

[![hackmd-github-sync-badge](https://hackmd.io/zAZmzYc5SZirLWTB-ZsNOw/badge)](https://hackmd.io/zAZmzYc5SZirLWTB-ZsNOw)

## Basic Info

- Primary mode of communications: #wg-data-compliance on [Filecoin Public Slack]()
    - async longform collab?
    - Slack versus Github Discussions?
- Meeting cadence: Every four weeks on Monday for now
- IPR regime: ?
- Confidentiality: opt-in for specific work items as needed but maximally transparent by default as per [PLN norms](https://protocol.ai/blog/announcing-the-permissive-license-stack/)
- Steward/Responsible Idiot: Juan Caballero, aka [bumblefudge](https://github.com/bumblefudge) on Filecoin Public Slack

## Meeting Notes

### 

### 3 Apr 2023, 8am PST 

- Agenda
    - Chair while Juan is out?
        - Ian will chair next, Juan will be back after that
    - Community and Governance Track at IPFS Thing: 
        - Opening talk (11-12): overview of all layers of IPFS governance, flag issues (will be recorded); unstructured time --> unconference
        - this group could propose a more specific session?
        - also happy to signal open topics anyone wants driven-by
        - Brainstormed a bit into [big questions section](https://hackmd.io/kL-J_4eOQj6Q1wS1T2JGZw?both#Big-Questions)
        - ![](https://hackmd.io/_uploads/B11RL_OZh.png) - 12-16, minus lunch = unconference slots
            + DDC session near the end of the slots, maybe?
    - Also at Thing: COmpact Format and [IPIP298](https://github.com/ipfs/specs/pull/340)
        - See also Hector San Juan's [IPIP383](https://github.com/ipfs/specs/pull/383) and [working prototype](https://github.com/hsanjuan/nopfs) for sideloading into kubo
        - See also Hector's [Design doc](https://www.notion.so/protocollabs/Content-blocking-on-IPFS-and-Kubo-3721f6fcc8044ba9acebd7356a60c4b7)
    - Filecoin Fdtn: Do we have a stopgap or for-now solution to GDPR?
        - Robin: [Euro Cloud CoC](https://eucoc.cloud/en/home) - self-regulation guidelines, might be applicable to Filecoin services?
        - Ian: Meeting with DPAs and regulators in coming weeks on behalf of Filecoin Foundation?
        - Ian: Steer away from PII use, cultural archives only
        - Robin: Non-custodial and disposable privkey narrative (end-user only data controller
            - caveat - demonstrable/provable deletion of privkey? quality of key mgmt is a factor
            - Marjorie - forgetting !== deletion (good-faith/reasonable effort to remove all access to data is usually enough BUT PER USE-CASE, not universal precedent)
        - Ian: Belgium has a lot of questions re: IPFS <> Solid-based citizen wallet/vault
            - extremely sensitive data/authoritative docs in that use-case...
            - Hybrid solution - Solid as identity/AuthZ layer, keep keys on that layer, IPFS just as logical storage under...
            - news flash - [that project is using MSFT azure/entra now](https://www.belganewsagency.eu/government-of-flanders-to-partner-with-microsoft-to-develop-data-vaults), with a tbd Solid integration??
            - Ian: Univ of Ghent is a powerhouse for Solid work
        - 

### 6 Mar 2023, 8am PST - Small Group Sync

- In Att: Robin, Juan, Boris, Ian
- Agenda
    - Intros
        - Ian: Filecoin Foundation partner engineer working with grantees; grantees' legal/compliance needs but also needs of PLN/FF
            - personal interest: legal feasibility of/gameplan for personal data stores
    - Shared Notes presi and invitation to edit
    - Thing Roadmap?
        - Get @lidel and @thibmeu in a room to discuss [IPIP298](https://github.com/ipfs/specs/pull/340) and blocklist ideas?
            - [ ] Boris will email them and see if they can host a session on this in governance/standards track and/or operators track
        - Short-term priorities versus Medium-term ones
            - Boris: Harmonizing on blocklists is most urgent tooling problem for both short-term pain and openinig up medium-term tooling possibilities
            - Ian: Incremental tooling - 
    - What tooling is most urgent?
        - 1 scan on upload (refuse to upload) versus 2 replication-filtering (refuse to serve) versus 3 storage liability, served or not (refuse to store) versus 4 DHT-accomplice risk (helping people find it even if you're not serving or storing)
            - Ian: We need to _start_ on #3 or else there's no backup if #1 and #2 fail
        - Filecoin variant:
            - for length of storage deal, data that's legal for creator and pinner might be downloadable to consumers in places where it isn't legal
            - data that is illegal to store might not be removable for the duration of the storage deal unless the storage provider is willing to lose FIL.
            - Boris: hypothesis: estuary might be a place where filtering could happen?
                - Ian: Estuary can choose not to serve...       
        - Robin: Is #4 in scope? Is IPNI liable for helping people find bad bits?
            - Ian: DNS precedent would say *mostly* no... Robin: But with exceptions (see counterterrorism policies in France, for ex.)
            - Robin: Caching proxies closer precedent to search on
            - Boris: but what about the rest of a block?
            - Robin: IANAL, we should get a real lawyer in here/on this
        - Boris: service provider <> protocol division of labor rears its head again here
            - Boris: estuary and CID gravity; might this have been part of why infura shut down their ipfs tooling?
            - Ian: web3s might have a lot of input here; Boris: They're using estuary too, but the architecture has some nuances
            - Boris: Pinata
            - Boris: what is kubo's recommendation ? where is ipfs desktop?
        - PDS issues
            - BlueSky/AT Protocol/DWN versus Pods/Solid
                - AT may be good to bring to the table when PDS is on the agenda
    - Fill out more sections in shared notes as time allows
        - figuring out the mode for input/shared ownership of the [shared-notes doc](https://hackmd.io/kL-J_4eOQj6Q1wS1T2JGZw?view)

### Kickoff - 5 Feb 2023, 8am PST
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
    - Addie: Network Goods; archelogical association (hypercerts, impact evaluation, other onchain opensource/funding mechanisms); worked on various L1s and FOSS before this
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