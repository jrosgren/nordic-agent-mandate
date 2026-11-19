Explainer · Published 19 November 2026 · JABB Consulting Oy Ab (Polkulab) · Status: research notes, not legal advice

# How can an AI agent prove it may act for a Nordic company?

AI agents are starting to place orders, accept terms and pay on behalf of businesses. The party on the other side then needs answers to four plain questions:

1. **Which company?** (a business ID in a national register)
2. **Who authorised the agent, and could that person bind the company?** (signing authority / representation rights)
3. **What exactly is the agent allowed to do?** (scope, amount, time limit)
4. **Is that authorisation still valid?** (revocation)

In Finland, Sweden and Norway, question 2 already has a legal answer: the national company registers record who may represent a company. Each country also runs a public mandate service built on those registers. This page maps that legal layer and the public services as they stand today, and notes where verifiable credentials and the EU wallets may fit. We are not proposing a new protocol or wallet here.

## 1. Where signing authority is recorded

|  | Finland | Sweden | Norway |
| --- | --- | --- | --- |
| Register | Trade Register (PRH), shown via YTJ | Bolagsverket (e.g. aktiebolagsregistret) | Enhetsregisteret / Foretaksregisteret (Brønnøysundregistrene) |
| Typical roles that can represent a company | Board members, managing director, procuration holders, other registered signatories (see the Suomi.fi list of Trade Register roles) | The board (always); *särskild firmatecknare* appointed by the board, alone or jointly ("i förening"); the VD for day-to-day management | The board; persons given *signatur* (all matters) or *prokura* (day-to-day operations); daglig leder for day-to-day matters |
| Free open data on representatives? | No. PRH's free open-data API (CC BY 4.0) does not include board, managing director or beneficial owners; that data is in PRH's paid information services. | No. Representatives are not part of Bolagsverket's free "valuable datasets" API; they are in Bolagsverket's paid company-information APIs. | Yes, partly. The open roles API returns role holders with name and date of birth; national identity numbers only via a Maskinporten-protected endpoint with restricted access. |

Sweden: the only restriction on signing authority that can be registered is that two or more persons must sign together ([FAR Online](https://www.faronline.se/dokument/rattserien/ratt-bolagsratt/s/rb_sarskildfirmatecknare/)). Amount limits, product limits and the like are therefore *not* visible in the register. They must live in a separate mandate (fullmakt). The same practical point applies to an agent: the register says who can bind the company, not what the agent may do.

## 2. The public mandate services built on those registers

### Finland – Suomi.fi e-Authorizations (DVV)

- Persons whose role in the Trade Register entitles them to represent the company can act for it without a separate mandate. Each e-service decides which roles it accepts.
- In a limited company, mandates are granted by the board members entered in the Trade Register, depending on the registered method of representation (e.g. the chair together with one board member). A "right to grant a mandate" can be delegated further.
- Mandates take effect immediately or at a chosen time. If a company cannot grant mandates itself, it can apply, and DVV processes the application.

### Sweden – Mina ombud

- A firmatecknare (or in some cases the VD) can grant a digital power of attorney at minaombud.se. If the person cannot sign alone, several must sign.
- The mandate is valid at the municipalities, agencies and other public organisations connected to the service, and the connected organisation decides which mandates can be created.
- Any firmatecknare can revoke a mandate the company granted, and the holder can hand it back.
- Bolagsverket develops and runs the service today. Digg and Bolagsverket have proposed moving it to Digg, with a working assumption of 2027.

### Norway – Altinn authorisation and system users (Digdir)

- Key roles in Enhetsregisteret (e.g. daglig leder, styrets leder) automatically get Altinn access packages such as *Hovedadministrator*, and can delegate access to others.
- Delegation in Altinn gives digital access. It does not change who holds the legal signature right recorded in the register.
- **Systembruker** (system user): a company can grant a vendor's registered system only the rights that system needs to act on its behalf for specific purposes, and can approve and withdraw those rights in Altinn. Of the three countries, this is the closest existing pattern to "software acting for a company under a scoped mandate".

## 3. Where verifiable credentials fit

- **eIDAS 2.0**, Regulation (EU) 2024/1183: Annex VI lists "powers and mandates to represent natural or legal persons" among the attributes that member states must make verifiable against authentic sources, for issuers of qualified electronic attestations of attributes.
- **National wallets.** DVV is building the Suomi.fi Wallet. Digg plans a first version of Sweden's state wallet, with a test environment for relying parties and attestation issuers, in December 2026, and names powers of attorney (fullmakter) among the documents the wallet should hold.
- **European Business Wallet**: the Commission's proposal COM(2025) 838 is aimed at companies. The Council adopted its negotiating position on 9 June 2026. The regulation is not yet adopted.
- **Formats**: the W3C Verifiable Credentials Data Model 2.0 has been a W3C Recommendation since 15 May 2025. Agent-payment work such as AP2 uses "mandates" to capture a user's conditions for autonomous purchases.

## 4. The gap we see (please correct us)

As far as we can tell from public documentation, the national services above are built for *public* e-services (Mina ombud, Suomi.fi) or for services inside a national platform (Altinn). We have not found a Nordic way for a *private* platform to receive a portable, machine-checkable statement of the form:

"Agent `X` may buy `Y` for company `Z` (business ID) up to `€N` until `date`. Granted by a person who holds signing authority for `Z` in the national register, and revocable."

The open questions are legal and practical, not cryptographic:

- Is a mandate to an AI agent a mandate to the company operating the agent, or to a named person responsible for it?
- How does joint signing ("two together", Trade Register representation methods) carry over to a machine-readable mandate?
- Which authentic source should a verifier trust, and what does a representative lookup cost in FI and SE, where the data is paid?
- How fast must revocation propagate for agent purchases?

We will keep this page updated as we learn. If you work on e-ID, mandates, company registers or agent commerce in the Nordics and think something here is wrong or missing, tell us. That is the most useful thing you can send.

## Waitlist and notes

Want our updates on Nordic agent mandates (FI, SE, NO): the legal mapping, register access and what we learn from e-ID and register teams? Join the waitlist by email. We sell nothing on this list, and it costs nothing.

[Join the waitlist (email)](mailto:ella@jabbconsulting.com?subject=%5BWAITLIST%5D%20Nordic%20agent%20mandate&body=Please%20add%20me%20to%20the%20Nordic%20agent%20mandate%20waitlist.%0A%0AName%3A%0AOrganisation%20(optional)%3A%0ACountry%20(FI%2FSE%2FNO%2Fother)%3A%0AWhat%20you%20would%20use%20an%20agent%20mandate%20for%20(optional)%3A)

Or write to [ella@jabbconsulting.com](mailto:ella@jabbconsulting.com) with the subject `[WAITLIST] Nordic agent mandate`.

**Privacy:** JABB Consulting Oy Ab is the controller. We keep your email address and anything you choose to write, only to send updates about this topic, for as long as you stay on the list. The legal basis is your consent (GDPR art. 6(1)(a)). We share the data with no one except our email provider (Microsoft 365). To leave, or to have your data deleted, reply "unsubscribe" or email ella@jabbconsulting.com at any time. You may complain to the Finnish Data Protection Ombudsman (tietosuoja.fi).

## Sources (opened 19 November 2026)

1. Suomi.fi: [How a company grants mandates](https://www.suomi.fi/instructions-and-support/e-authorizations/using-suomifi-e-authorizations-as-an-organisation/granting-mandates-as-an-organisation/how-a-company-grants-mandates); [Acting on behalf of a Finnish company without a separate mandate](https://www.suomi.fi/instructions-and-support/e-authorizations/acting-on-behalf-of-an-organisation/acting-on-behalf-of-a-finnish-company-or-self-employed-person-without-a-separate-mandate)
2. PRH open data: [avoindata.prh.fi](https://avoindata.prh.fi/en) (licence and API scope); PRH [information services](https://www.prh.fi/en/companiesandorganisations/tietopalvelut.html)
3. Mina ombud: [Frågor och svar](https://minaombud.se/info/fragor-och-svar); [Om oss](https://minaombud.se/info/om-oss); Digg [Budgetunderlag 2026–2028](https://www.digg.se/download/18.7aec96c71954b58e82831/1740731018828/Budgetunderlag%202026-2028.pdf) (section 2.7)
4. Firmateckning: [FAR Online – Firmatecknare](https://www.faronline.se/dokument/rattserien/ratt-bolagsratt/f/rb_firmatecknare/); [Särskild firmatecknare](https://www.faronline.se/dokument/rattserien/ratt-bolagsratt/s/rb_sarskildfirmatecknare/); [Upphandlingsmyndigheten](https://www.upphandlingsmyndigheten.se/frageportalen/3224061/aktiebolag-som-ska-teckna-telefon-abonnemang/); Bolagsverket [open data](https://bolagsverket.se/apierochoppnadata/hamtaforetagsinformation/nedladdningsbarafiler.2517.html)
5. Brønnøysundregistrene: [Enhetsregisteret API documentation](https://data.brreg.no/enhetsregisteret/api/dokumentasjon/no/); [Roller i virksomheten](https://www.brreg.no/bruke-data-fra-bronnoysundregistrene/datasett-og-api/roller-i-virksomheten/)
6. Altinn: [Hvem kan administrere fullmakter?](https://info.altinn.no/hjelp/ny-tilgangsstyring/tilgangspakker/roller-fra-enhetsregisteret-for-a-administrere-tilganger/); [Drift av aksjeselskap (signatur, prokura)](https://info.altinn.no/starte-og-drive/drive-bedrift/drift-og-administrasjon/drift-av-aksjeselskap/); Digdir [Systembruker for virksomheter](https://docs.digdir.no/docs/Maskinporten/maskinporten_func_systembruker.html)
7. eIDAS 2.0: [Regulation (EU) 2024/1183](https://eur-lex.europa.eu/eli/reg/2024/1183/oj/eng) (Annex VI, item 9)
8. Wallets: DVV press release 5 June 2026 on the [Suomi.fi Wallet](https://www.sttinfo.fi/tiedote/72108203/digital-and-population-data-services-agency-seeking-a-technical-implementation-partner-for-the-new-suomifi-wallet?lang=en&publisherId=3777); Digg 15 April 2026, [Stegvis utveckling för den digitala identitetsplånboken](https://www.digg.se/om-oss/nyheter/digital-identitet/nyheter/2026-04-15-stegvis-utveckling-for-den-digitala-identitetsplanboken)
9. European Business Wallet: [COM(2025) 838](https://www.europarl.europa.eu/RegData/docs_autres_institutions/commission_europeenne/com/2025/0838/COM_COM(2025)0838_EN.pdf); Council, [9 June 2026](https://www.consilium.europa.eu/en/press/press-releases/2026/06/09/european-business-wallets-council-adopts-negotiating-position/)
10. W3C [Verifiable Credentials Data Model 2.0](https://www.w3.org/TR/vc-data-model-2.0/); [AP2](https://ap2-protocol.org/)

Published by **JABB Consulting Oy Ab** (Polkulab), Business ID 2497134-6, Vikingavägen 45, 65200 Vasa, Finland. Contact: [ella@jabbconsulting.com](mailto:ella@jabbconsulting.com). Ella is an AI assistant who works for JABB Consulting. This page summarises public sources and is not legal advice. Registers and services named here are not affiliated with us and do not endorse this page.

---
Styled version of this page: https://raw.githack.com/jrosgren/nordic-agent-mandate/main/index.html

