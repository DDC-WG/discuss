# DDC WG Shared Notes

[![hackmd-github-sync-badge](https://hackmd.io/kL-J_4eOQj6Q1wS1T2JGZw/badge)](https://hackmd.io/kL-J_4eOQj6Q1wS1T2JGZw)


How to use this document:
- Please give it a quick skim-through to get the hang of the format and function before editing
- feel free to add pointers, links, open questions, in amongst the others
    - big chunks of text and screengrabs (can be CTRL-V'd straight into hackmd btw) should go at the end of sections, below open questions
- eventually, as sections get unwieldy or too detailed for this structure, we'll move them out into their own documents
- hackmd comments are kind of unwieldy, but feel free to @ people in new comments indented below the ones you're asking about

## Mapping the problem space

### Roles / Actor Model for IPFS

Notes:
- not as linear as it looks, just numbered to have some basic directionality for up/downstream dependencies where applicable
- ymmv/feedback welcome

|#|Role|Comments|
|---|---|---|
|1|subject of data||
|2|creator of data||
|3|uploader of data||
|4|pinner of data|Note: this role is often redundant, i.e. self-pin + redundant service provider = shared obligations|
|5|propagator/replicator of data|Note: in filecoin context, payer of storage contract and payee usually two actors|
|6|server of data [to consumer]||
|7|DHT router of data|helps consumer route request|
|8|consumer of data||

### Privacy Threat Model

Notes:
- the idea here is that modelling the threats to people's privacy (rather than to people's privacy rights) is important, has significant overlap with people's rights, and often provides a better way to think about how to implement rights (or not have to implement them in the first place because they are respected at the tech layer)
- copyright liabilities versus CSAM liabilities and counterterrorism liabilities
- lots to take from https://github.com/protocol/ResNetLab/blob/master/OPEN_PROBLEMS/PRESERVE_USER_PRIVACY.md and https://github.com/gpestana/notes/issues/3

(actual model TBD but could dive deeper into the roles above)

### Big Questions

- How can the IPFS ecosystem or analogous P2P/decentralized ones structure liabilities and contracts?
- The "bad bits" question, viewed legally: FOUR distinct points of potential intervention
    1. scan on upload (refuse to upload) versus 
    2. replication-filtering (refuse to serve) versus 
    3. storage liability, served or not (refuse to store) versus 
    4. DHT-accomplice risk, i.e. helping people find it even if you're not serving or storing (refuse to route)
- Where to even start with that, operationally?
    - Even if others are more urgent, we need to _start_ working on #3 in parallel because it will be key to have a backup if #1 and #2 fail
    - Is #4 necessarily as important if others are well-actioned?
        - how are bad bits tombstoned?
    - Filecoin variant on the 4 refusals model:
        - for length of storage deal, data that's legal for creator and pinner might be downloadable for consumers in places where that same content it isn't legal
        - data that is illegal to store might not be removable for the duration of the storage deal unless the storage provider is willing to lose FIL (i.e. there as incentive for #3 to be circumscribed or excepted where 2 is good enough in the current system's contracts)
    - hypothesis: estuary might be a place to start thinking about filtering first/soonest?

- Rulesets for a composable policy engine?
    - geography of originator and/or subject
    - age of originator and/or subject
    - geography of operator/service
    - use-case/subject-matter stuff (i.e. HIPAA)
    - international baselines/lowest-common denom (CSAM + Terrorism)
        - CID matches hash-based CSAM and Terrorism and (C) 
            - Robin - some use Perceptual Hashing  or multi-hashes (cf. [ISCC](https://iscc.codes/features/#content-variant-detection))
            - Juan: maybe better at ingress than at point of hosting...
            - Ian: but who's responsible and who should be checking? How enforce?
                - Economics? Robin: What if [say, post-facto] perceptual hashing were done as part of Proof-of-Storage? Ian: Proof-of-COMPLIANT-Storage? Robin: Let's no overpromise, more like Proof-of-Spot-Checked-Storage
                - 

## Compliance Areas

### GDPR & GDPR-like Regulations

- who is data controller
- who is data processor
  - RB: will read through EDPB guidance to list criteria we could apply
- deletion rights
- access rights
- tracking over the DHT
    - does someone broadcasting and/or querying have any obligation?
    - should tracking be penalized (technically) or policed (by human oversight)?
- right to be forgotten
- data sovereignty and data localization
- who is the supervisory authority
- can we get the EDPB or a DPA which we could talk to?

### CCPA & CCPA-like Regulations

- `1798.120` - opt-out of data "sale" (incl. advertising and profiling)
    + Operative 1Jan 2023
    + Official FAQ [here](https://oag.ca.gov/privacy/ccpa#sectionb)
    + Statute [here](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.120.)
- `1798.121` - opt-out of "sensitive personal information"
    + Operative 1Jan 2023
    + Rules still being finalized, no enforcement precedent yet
    + Statute [here](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.121.)
- The specific concern here is under what (if any) conditions might sharing data as part of an IPFS system (eg. advertising to the DHT) count as a sale of data (or sharing of sensitive data) under the CPRA. I *think* it doesn't, but we should put it to the test.
- CCPA <> GPC

### Global Privacy Control (GPC)

- browser spec for enabling the opt-outs defined by CCPA
    - "Is GPC the new 'do not track'?", Anokhy Desai, [IAPP](https://iapp.org/news/a/is-gpc-the-new-do-not-track/)
- Dev'd by W3C [Privacy CG](https://privacycg.github.io/)
    - [spec here](https://privacycg.github.io/gpc-spec/)
- Support without extensions
    - Brave
    - Firefox (stable since dec '21)
    - DuckDuckGo

### Digital Services Act (DSA)

- Overview
    - [Statute here](https://commission.europa.eu/document/download/c33fa400-f978-402f-b530-81e10ff09dd7_en)
    - [Mastroshka](https://commission.europa.eu/strategy-and-policy/priorities-2019-2024/europe-fit-digital-age/digital-services-act-ensuring-safe-and-accountable-online-environment_en#which-providers-are-covered) Mental model of "who's in the crosshairs" - global-scale infra and "hosting" concerns are conceived as necessarily in-scope, even if not the primary targets
- Open Question for the group: How can businesses building on IPFS have certainty of which category they'll fall into, and thus, what their obligations under DSA will be?

![Screengrab from obligations chart here: https://commission.europa.eu/strategy-and-policy/priorities-2019-2024/europe-fit-digital-age/digital-services-act-ensuring-safe-and-accountable-online-environment_en#documents](https://hackmd.io/_uploads/HJYRZd7kn.png)

### Digital Markets Act (DMA)

- Overview
    - Anti-trust/economic component of DSA+DMA voltron
    - [press release](https://ec.europa.eu/commission/presscorner/detail/en/ip_22_6423)
    - [FAQ](https://ec.europa.eu/commission/presscorner/detail/en/QANDA_20_2349)
    - [Status]()
- Open Questions for the group:
    - how can we make sure no networks get tagged as a "Gatekeeper"?
    - portability requirements - do end-users get some kind of portal for downloading-before-deleting their particular bundle of CIDs?
        - ![screengrab from data portability channel on MyData Slack](https://hackmd.io/_uploads/HJizAi7Cj.png)

> Specifically, there are three main cumulative criteria that bring a company under the scope of the DMA:
> 1. A size that impacts the internal market: this is presumed to be the case if the company achieves an annual Union turnover equal to or above €7.5 billion in in each of the last three financial years, or where its average market capitalisation or equivalent fair market value amounted to at least €75 billion in the last financial year, and it provides a core platform service in at least three Member States;
> 2. The control of an important gateway for business users towards final consumers: this is presumed to be the case if the company operates a core platform service with more than 45 million monthly active end users established or located in the EU and more than 10,000 yearly active business users established in the EU in the last financial year;
> 3. An entrenched and durable position: this is presumed to be the case if the company met the second criterion in each of the last three financial years.
Companies that satisfy the above criteria are presumed gatekeepers but have the opportunity to rebut the presumption and submit substantiated arguments to demonstrate that due to exceptional circumstances they should not be designated as a gatekeeper despite meeting all the thresholds.

([Src: 2023 EurCom Q&A](https://ec.europa.eu/commission/presscorner/detail/en/QANDA_20_2349))

### Terrorism Content

### CSAM

- US Framework
    - Statute: [USC title 18, part 1, chapter110, §2258A](https://uscode.house.gov/view.xhtml?req=granuleid:USC-prelim-title18-section2258A&num=0&edition=prelim)
    - [Congressional Research Report March '22](https://crsreports.congress.gov/product/pdf/LSB/LSB10713)
- EU Centre on CSA 
    + [press release May '22](https://ec.europa.eu/commission/presscorner/detail/en/IP_22_2976)
    + [very critical Q&A on^ in Berlin, Feb '23](https://www.bundestag.de/resource/blob/935812/c33b127246a5dabdd19f3d01627f6f4b/Stellungnahme-Jakubowska-data.pdf)

> The statutory scheme has created perverse disincentives for providers to engage in content safety work that would give them knowledge of CSAM violations on their platforms. Providers have no obligation to monitor their platforms or scan for CSAM and face no statutory liability in refusing to do so. Providers who do elect to implement thorough content safety programs may be exposed to liability. Further, providers who engage in content safety verification and human review risk discovery requests from criminal defendants regarding their detection practices. In addition, content safety reviewers are exposed repeatedly to horrific imagery, impacting resiliency and retention rates for employees and contractors.

(Src: American Bar Association [blog post](https://www.americanbar.org/groups/gpsolo/publications/gp_solo/2021/november-december/addressing-increase-online-child-sexual-abuse-pandemic/), Dec '21)

### Malware and Ransomware

- See [malware precedents section of bibliography](#malware-precedents)

## Open Questions for Discussion

Theorizing
- Do we have a legal theory of data rights in distributed systems?



Operationalizing Compliance and Management (partic long-tail)
- Should we create a GDPR Art 40/41 code of conduct?
    - https://scope-europe.eu/en/projects/eu-cloud-code-of-conduct/
- Are there co-op rules that would make sense for some of this?
    - Ian: composability of geo-diverse and/or use-case specific rulesets may work with federated enforcement
        - heirarchy/precedence for layering policies/rulesets

# References

## Appendix A: Glossary

## Appendex B: Ecosystem Map

Key players in the PLN
- browsers and ecosystem team
    - Robin @robin-berjon 
- filecoin foundation
    - represented now by @ianconsolata and occasionally by Danny o'b
- bad bits 
    - no real POC/point-person 
    - IPFS operators community of practice, cloudflare, etc have been crowd-working this front
        - [cloudflare PR](https://github.com/ipfs/kubo/issues/8492) on kubo? lua & nginx
            - [IPIP](https://github.com/ipfs/specs/pull/340)
        - ad hoc rulesets, rather than pro-active framework
        - might be good to invite someone from Cloudflare who worked on the IPFS gateway policy to a future, pre-agenda'd meeting on these topics
        - ipfs.io has a toolset as well
- saturn/fil teams
    - saturn project represented here by @gruns (Ansgar Grunseid)
    - filecoin station represented by @juliangruber (Julian Gruber)
- pinning services:
    - web3storage
    - pinata
    - etc

Key players outside it:
- Cloudflare research team
- grantees of FF, web3 projects using ipfs via pinning services, ceramic network, and/or filecoin
- "competitive landscape" (from ipfs docs) - [feature matrix](https://docs.ipfs.tech/concepts/comparisons/#comparing-the-key-features-of-other-solutions-to-ipfs)

## Appendix C: Anatomy of IPFS Network

![map of IPFS components from github/ipfs/kubo/readme](https://camo.githubusercontent.com/05362f4ab9e7c512338a589145f704f6f0dcea273c64b63628072b86e304e3f5/68747470733a2f2f646f63732e676f6f676c652e636f6d2f64726177696e67732f642f652f32504143582d3176535f6e3146765375366d646d5369726b427249494569623267716867746174443961776150325f576472474e347a544e65673632305851643950393557542d49766f676e5378494964434d3575452f7075623f773d3134343626683d31303336)

Different business models involve running different parts of this architecture. Theories vary as to how much access and "insight" an operator has to have into the data they're replicating, hosting, and/or persisting; in some cases, it MAY be worth getting into the weeds on UnixFS versus WNFS, decryption keys being delegated where, etc.

## Appendix D: Bibliography

General academic biblio that may be useful
- Peer-to-Peer System Design Trade-Offs: A Framework Exploring the Balance between Blockchain and IPFS, Tenorio-Fornés, A. et al., Oct '21. [Mdpi.com](https://www.mdpi.com/2076-3417/11/21/10012)

### Malware Precedents

- 2021 go C2 malware spread across ipfs, [Anomili.com](https://www.anomali.com/blog/the-interplanetary-storm-new-malware-in-wild-using-interplanetary-file-systems-ipfs-p2p-network)
- Overview of IPFS-based malware and phishing methods. [talos](https://blog.talosintelligence.com/ipfs-abuse/)