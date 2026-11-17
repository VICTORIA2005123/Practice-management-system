# Literature survey

This survey covers twelve research papers from 2022 to 2026 and five software products a CA firm could buy instead. For each paper it records what the authors did, what they found, and where their work stops short of what a small Indian CA firm needs. The research gap at the end points back to specific rows of the tables.

## How the papers were chosen

- Published between 2022 and 2026, in a peer-reviewed journal or conference.
- Each one checked against Crossref by its DOI, so every reference below exists and its details are correct.
- Each one about one of the things this project touches: technology in accounting firms, automating accounting work, GST compliance in India, audit trails, data protection, digital certificates, or workflow systems.
- For each paper the limitation column says whether the authors state the limitation themselves (**stated**) or whether it is my reading of how the paper applies to a small CA firm (**my reading**).

## Comparison of previous work

| # | Paper (author, year) | Method used | Data | Results | Limitations |
|---|---|---|---|---|---|
| 1 | Januszewski and Buchalska-Sugajska, 2023 [1] | Literature review, two surveys and interviews | Accounting firms and their SME clients in Poland | 1 in 3 clients send documents electronically. Half the firms use robotic process automation (RPA). | Stated: accounting firms serving SMEs are under-researched. My reading: about document flow, not filing deadlines. Polish context. |
| 2 | Thottoli, 2022 [2] | Questionnaire, PLS-SEM | 88 practising chartered accountants in Kerala | IT training and perceived usefulness drive IT adoption by CAs | My reading: small sample from one state. Looks at audit software only, not tools for running the office. |
| 3 | Perdana, Lee and Kim, 2023 [3] | Built and tested RPA prototypes for four audit tasks | Real tasks from Big 4 and mid-sized firms | RPA cuts time and errors on repetitive, rule-based audit work | My reading: aimed at large audit firms. Doesn't cover recurring GST, TDS or income-tax work. |
| 4 | Kassar and Jizi, 2026 [4] | Systematic literature review | Studies from 2016 to 2022 | Benefits of AI and RPA in accounting are financial, operational and in reporting quality. Practitioners resist, mainly from fear of losing jobs. | My reading: nothing after 2022, nothing specific to India or small firms. |
| 5 | Jena, 2026 [5] | Survey using the TOE and TAM models, PLS-SEM | Accountants in India | Security, readiness, competitive advantage and government support drive intention to adopt cloud accounting | Stated: Indian accountants have under-used cloud accounting. My reading: measures intention, not actual use. |
| 6 | Basavanagouda and Panduranga, 2022 [6] | Survey with factor analysis | GST practitioners in India | Taxpayers hand their GST compliance over to practitioners. GST is hard for taxpayers who aren't comfortable with technology. | My reading: describes the burden on practitioners but proposes no tool to carry it. |
| 7 | Alagha and Ozcelik, 2025 [7] | Designed and evaluated a blockchain audit trail | Simulated transactions | Checking a record stays fast as volume grows | Stated: traditional audit trails are costly and open to tampering. My reading: a blockchain is more than a small firm needs. A database-written log does the job. |
| 8 | Sonkar, 2025 [8] | Legal analysis comparing the DPDP Act with GDPR, CCPA and others | Statute texts | Real progress, with gaps in government exemptions and the Board's independence | Stated: heavy compliance burden on small businesses. My reading: no evidence from actual firms. |
| 9 | Mladinić, Vukić and Rončević, 2023 [9] | Online survey | 345 small and medium firms in Croatia | Small firms understand data-protection duties poorly and lack people and money to comply | My reading: EU and GDPR, not India. Shows what happens when small firms get no tooling. |
| 10 | Berbecaru and Lioy, 2023 [10] | Measured certificates of the top 1 million websites, tested browsers | Web certificates, August 2021 | Browsers check certificate revocation incorrectly or incompletely | My reading: about website certificates, not signing DSCs on USB tokens. |
| 11 | Sheri and Jadav, 2025 [11] | Built and deployed an automated certificate-renewal framework | One mid-sized organisation | Stated: tracking certificates by hand or in spreadsheets causes outages. Automation improved reliability. | My reading: server certificates renew themselves. An Indian DSC needs a person to re-verify, so software can only track and warn. |
| 12 | Flechsig, Völker, Egger and Weske, 2022 [12] | 20 expert interviews, then a platform design | Requirements from interviews | Combining workflow management with RPA needs one integrated platform | My reading: built for large enterprises, too heavy for a 10-person office, and has no idea of statutory deadlines. |

## What the papers say, in plain words

**Small firms are slow to adopt technology, and the reasons are known.** Papers 2 and 5 both study Indian accountants. Training, readiness and trust in security decide whether a firm adopts a tool, more than how useful the tool is on paper. So a system for a small firm has to be easy to learn and has to show it is secure. That's why this project has two-factor sign-in and keyboard shortcuts that mirror how accountants already work in Tally.

**Automation pays off on repetitive, rule-based work.** Papers 1, 3 and 4 find that RPA saves time and errors on exactly that kind of work. Recurring compliance is the clearest example in a CA firm: the same return, for the same client, every month, with a due date set by law. But all three studies look at large firms or at document handling, and none of them looks at the calendar of filings itself.

**GST moved compliance work onto practitioners.** Paper 6 finds that taxpayers hand their GST compliance over to practitioners. That's the firm this project serves. The paper describes the burden but stops there, with no tool to carry it.

**Spreadsheets are a known cause of certificate failures.** Paper 11 says this in so many words: certificates tracked by hand or in spreadsheets expire and cause outages. Paper 10 shows that even large systems check certificates badly. A CA firm's DSCs differ from website certificates in one important way. A DSC can't renew itself, because a person has to re-verify their identity with the certifying authority. So the right design is to track and warn early, not to automate the renewal.

**An audit trail has to be hard to skip.** Paper 7 argues that ordinary audit trails can be tampered with or skipped, and answers with a blockchain. For one firm with one database, that's far more than needed. The same goal, a trail no part of the application can skip, is met by having the database itself write the trail through triggers.

**Small businesses struggle with data-protection law.** Paper 9 shows that small firms in the EU understand GDPR poorly and lack the money to comply. Paper 8 warns that India's DPDP Act puts a heavy burden on small businesses. A CA firm is a small business holding very sensitive data. If the system builds the duties in (encryption, logging who saw what, a fixed retention period), the firm complies without hiring anyone.

**Workflow platforms exist, but for big companies.** Paper 12 designs a platform that joins workflow management with RPA. It's built for enterprises with IT departments. A 10-person CA office needs the workflow without the platform.

## Existing products

Checked on each product's own website in November 2026. "Not shown" means the site doesn't mention the feature, not that it definitely doesn't exist.

| Product | What it is | Indian recurring compliance (GST, TDS, ITR) | DSC expiry tracking | Audit trail | Pricing |
|---|---|---|---|---|---|
| TallyPrime | Accounting, inventory and GST software for a business's own books | Files a business's own GST and TDS. Not a calendar of a firm's clients. | Not shown | Yes, an edit log of every change | From Rs 750 a month, or Rs 22,500 once, plus GST |
| CompuOffice (CompuTax) | Desktop suite for Indian tax professionals: ITR, TDS, GST, ROC forms | Partly: shows filed and pending returns. Scheduling recurring work not shown. | Not shown | Not shown | Not published |
| Zoho Practice | Cloud practice management for accounting firms | Generic task automation. The only filings it names are UK ones. | Not shown | Not shown | $49 to $149 a month per firm |
| Karbon | Cloud practice management and workflow, from the US | Generic recurring jobs. No Indian filings shown. | Not shown | Activity timelines | $59 to $89 a month per user |
| TaxDome | All-in-one platform for tax firms, from the US | Generic recurring workflows. No Indian filings shown. | Not shown | Yes, firm-wide activity feed | Per client or per user, in dollars |

Sources: [tallysolutions.com](https://tallysolutions.com/tally-prime/), [computax.in](https://www.computax.in/product/compuoffice-tax-automation-software), [zoho.com/practice](https://www.zoho.com/practice/), [karbonhq.com/pricing](https://karbonhq.com/pricing/), [taxdome.com/pricing](https://taxdome.com/pricing). TaxDome's site blocked automated reading, so its row came from search excerpts of its pages. Check it in a browser before the review.

**What this table shows.** The tools split in two. Indian tools (Tally, CompuOffice) prepare returns and keep books, but they don't run the office: they don't create next month's work, track who has it, or warn about DSCs. Foreign tools (Zoho Practice, Karbon, TaxDome) run the office, but they know nothing about GSTR-3B, TDS quarters or Indian DSCs, and they're priced in dollars per user. None of the five tracks DSC expiry.

## Research gap

The papers on automation in accounting (rows 1, 3 and 4) study large firms and document handling, not the calendar of statutory filings. The one paper on GST practice (row 6) describes the burden on practitioners but offers no tool. The papers on certificates (rows 10 and 11) show that spreadsheet tracking causes expiries, but study website certificates that renew themselves, not DSCs that need a person. In the product table, the Indian tools don't run the office and the foreign tools don't know Indian compliance, and none tracks DSC expiry.

**No reviewed work or product combines, for a small Indian CA firm, automatic creation of recurring GST, TDS and income-tax work, DSC expiry warnings, and an audit trail that the application cannot skip.** This project fills that gap.

## Sustainability and ethics in the literature

- **Jobs.** Paper 4 finds that practitioners resist automation mainly from fear of losing their jobs. This project automates the bookkeeping of the work (creating tasks, tracking dates), not the professional work of preparing and checking returns. The [SDG page](05-sdg-mapping.md) takes this up under SDG 8.
- **Small businesses and the law.** Papers 8 and 9 show that data-protection law weighs heaviest on small firms. Building the safeguards into the tool is what makes compliance affordable for them.
- **Formal economy.** Paper 6 shows GST compliance flowing through practitioners. Helping them file on time keeps their small-business clients compliant, which is SDG targets 8.3 and 17.1.
- **Proportionate technology.** Papers 7 and 12 propose heavy solutions (blockchain, enterprise platforms). Choosing a plain database and browser app over these is itself a sustainability choice: lower cost, less energy, and something a small firm can run.

## References

[1] A. Januszewski and N. Buchalska-Sugajska, "Digital transformation in accounting firms in Poland," *Procedia Computer Science*, vol. 225, pp. 1621–1631, 2023, doi: 10.1016/j.procs.2023.10.151.

[2] M. M. Thottoli, "Toward a link between IT determinants and their adoption: Empirical analysis based on practicing chartered accountants," *Indonesian Journal of Sustainability Accounting and Management*, vol. 6, no. 1, 2022, doi: 10.28992/ijsam.v6i1.461.

[3] A. Perdana, W. E. Lee, and C. M. Kim, "Prototyping and implementing robotic process automation in accounting firms: Benefits, challenges and opportunities to audit automation," *International Journal of Accounting Information Systems*, vol. 51, Art. no. 100641, 2023, doi: 10.1016/j.accinf.2023.100641.

[4] M. Kassar and M. Jizi, "Artificial intelligence and robotic process automation in auditing and accounting: A systematic literature review," *Journal of Applied Accounting Research*, vol. 27, no. 1, pp. 217–241, 2026, doi: 10.1108/JAAR-05-2024-0175.

[5] R. K. Jena, "Technology and accounting convergence: Factors influencing cloud accounting information systems adoption by accountants in the era of accounting 4.0," *Revista de Contabilidad – Spanish Accounting Review*, pp. 1–20, 2026, doi: 10.1108/SAR-05-2026-0069.

[6] Basavanagouda and V. Panduranga, "Perspectives and role of GST practitioners in promoting GST compliance in India," *Vision: The Journal of Business Perspective*, 2022, doi: 10.1177/09722629221114604.

[7] B. Alagha and I. Ozcelik, "BEATS: Practical audit trail in blockchain systems," *IEEE Access*, vol. 13, pp. 109657–109669, 2025, doi: 10.1109/ACCESS.2025.3582722.

[8] A. Sonkar, "The Digital Personal Data Protection Act, 2023: Analysing its implications, challenges, and future prospects," *International Cybersecurity Law Review*, vol. 6, no. 4, pp. 547–569, 2025, doi: 10.1365/s43439-025-00164-2.

[9] A. Mladinić, Z. Vukić, and A. Rončević, "GDPR compliance challenges in Croatian micro, small and medium sized enterprises," *Pravni vjesnik*, vol. 39, no. 3–4, pp. 53–75, 2023, doi: 10.25234/pv/23972.

[10] D. G. Berbecaru and A. Lioy, "An evaluation of X.509 certificate revocation and related privacy issues in the web PKI ecosystem," *IEEE Access*, vol. 11, pp. 79156–79175, 2023, doi: 10.1109/ACCESS.2023.3299357.

[11] U. R. Sheri and V. Jadav, "Enterprise-scale SSL/TLS automation using Let's Encrypt: A practical framework for certificate lifecycle management," in *Proc. 2025 Int. Conf. Computer and Applications (ICCA)*, 2025, pp. 1–6, doi: 10.1109/ICCA66035.2025.11430913.

[12] C. Flechsig, M. Völker, C. Egger, and M. Weske, "Towards an integrated platform for business process management systems and robotic process automation," in *Business Process Management: Blockchain, RPA and CEE Forum*, LNBIP vol. 459, Springer, 2022, pp. 138–153, doi: 10.1007/978-3-031-16168-1_9.
