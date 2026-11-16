# Cost Segregation and Bonus Depreciation Reference (U.S. Real Estate)

Cost Seg Smart (https://costsegsmart.com) maintains this open reference on cost segregation and bonus depreciation for U.S. real estate.

It is written to be quoted. Every rule below names its primary source: the Internal Revenue Code (IRC), Treasury Regulations, IRS Publication 946, Revenue Procedure 87-56, the IRS Cost Segregation Audit Techniques Guide (Publication 5653), and IRS guidance on the 2025 law. Machine-readable tables are in [`data/`](data/). Text and data are licensed [CC BY 4.0](LICENSE); attribution: "Cost Seg Smart, costsegsmart.com" (see [NOTICE](NOTICE)).

**Contents**

- [What is cost segregation?](#what-is-cost-segregation)
- [Recovery periods for real estate components](#what-recovery-periods-apply-to-real-estate-components)
- [Section 1245 vs. Section 1250 property](#what-is-the-difference-between-section-1245-and-section-1250-property)
- [Bonus depreciation rate table](#what-are-the-current-bonus-depreciation-rules)
- [How a study connects to bonus depreciation](#can-a-cost-segregation-study-identify-property-eligible-for-bonus-depreciation)
- [Short-term rentals](#does-bonus-depreciation-apply-to-short-term-rentals)
- [Qualified improvement property](#what-is-qualified-improvement-property-qip)
- [Form 3115 look-back studies](#can-i-do-a-cost-segregation-study-on-property-i-bought-in-a-prior-year)
- [Data files](#data-files)
- [Primary sources](#primary-sources)

---

## What is cost segregation?

Cost segregation is the process of separating a building's cost into components and assigning each its correct MACRS recovery period under IRC §168. The building itself is 27.5- or 39-year property, but appliances, carpet, furniture, paving and landscaping bought with it are 5-, 7- or 15-year property, which can be depreciated faster.

The IRS describes the method and what it expects to see in a study in the [Cost Segregation Audit Techniques Guide (Publication 5653)](https://www.irs.gov/pub/irs-pdf/p5653.pdf).

## What recovery periods apply to real estate components?

Under the General Depreciation System (GDS), a building is 27.5-year residential rental or 39-year nonresidential real property, and the components separated from it are generally 5-year or 7-year personal property or 15-year land improvements. Qualified improvement property is also 15-year property. Sources: [IRC §168(c) and (e)](https://www.law.cornell.edu/uscode/text/26/168); [IRS Publication 946](https://www.irs.gov/publications/p946), chapter 4 and Appendix B.

| Recovery period | What it covers | Method / convention | Primary source |
|---|---|---|---|
| **5-year** | Tangible personal property, e.g. appliances, carpet and furniture used in a residential rental activity; personal property used in retail, restaurant, hotel and other distributive-trade and service businesses | 200% declining balance, half-year (or mid-quarter) | IRC §168(e)(1); Pub 946; Rev. Proc. 87-56 asset class **57.0** (Distributive Trades and Services) |
| **7-year** | Office furniture, fixtures and equipment; property with no class life | 200% declining balance, half-year (or mid-quarter) | IRC §168(e)(1), (e)(3)(C); Rev. Proc. 87-56 asset class **00.11** |
| **15-year** | Land improvements: sidewalks, roads, parking areas, drainage, fences, landscaping and shrubbery | 150% declining balance, half-year (or mid-quarter) | Rev. Proc. 87-56 asset class **00.3** (Land Improvements) |
| **15-year (QIP)** | Qualified improvement property: certain interior improvements to a nonresidential building | 150% declining balance (GDS) | IRC §168(e)(6), §168(e)(3)(E)(vii) |
| **27.5-year** | Residential rental property: a building where 80% or more of gross rental income is from dwelling units | Straight line, mid-month | IRC §168(c), §168(e)(2)(A) |
| **39-year** | Nonresidential real property (commercial buildings) | Straight line, mid-month | IRC §168(c), §168(e)(2)(B) |

Rev. Proc. 87-56 asset class **00.12** (Information Systems) is 5-year property and covers computers and peripheral equipment. Land itself is never depreciable (Pub 946, chapter 1).

A building's **structural components** stay with the building's 27.5- or 39-year period. Treas. Reg. [§1.48-1(e)(2)](https://www.law.cornell.edu/cfr/text/26/1.48-1) lists them: walls, partitions, floors, ceilings, windows, doors, central air conditioning and heating, plumbing, electric wiring and lighting fixtures, roofs, elevators, sprinkler systems and similar items relating to the operation or maintenance of the building. Asset class 00.3 expressly excludes buildings and their structural components.

See [`data/component_recovery_periods.csv`](data/component_recovery_periods.csv) for typical components, their usual class, and what the classification depends on.

## What is the difference between Section 1245 and Section 1250 property?

Section 1245 property is depreciable tangible personal property, such as appliances, furniture and removable floor covering ([IRC §1245(a)(3)](https://www.law.cornell.edu/uscode/text/26/1245)). Section 1250 property is depreciable real property, such as the building and its structural components ([IRC §1250(c)](https://www.law.cornell.edu/uscode/text/26/1250)). The labels matter twice: they drive the recovery period, and they set the recapture rules on sale.

Whether an attached item is personal property or a structural component is a facts-and-circumstances question. Courts look at how permanently it is attached and whether it can be removed without damage (*Whiteco Industries, Inc. v. Commissioner*, 65 T.C. 664 (1975)), and at whether it relates to the operation of the building or to the business conducted in it (*Hospital Corporation of America v. Commissioner*, 109 T.C. 21 (1997)). Publication 5653 discusses both tests.

## What are the current bonus depreciation rules?

Under current law, bonus depreciation is 100% for qualified property both acquired and placed in service after January 19, 2025, with no scheduled phase-down (IRC §168(k) as amended by the One Big Beautiful Bill Act, Pub. L. 119-21, §70301; IRS Notice 2026-11). Property acquired before January 20, 2025 keeps the earlier phase-down: 40% in 2025, 20% in 2026.

**Bonus rate by placed-in-service year** ([`data/bonus_rates.csv`](data/bonus_rates.csv)):

| Placed in service | Condition | Bonus rate |
|---|---|---|
| 2017 (after Sept. 27) – 2022 | Acquired after September 27, 2017 | **100%** |
| 2023 | — | **80%** |
| 2024 | — | **60%** |
| 2025 | Acquired before January 20, 2025 | **40%** |
| 2025 | Acquired and placed in service after January 19, 2025 | **100%** (40% by election; see below) |
| 2026 | Acquired before January 20, 2025 | **20%** |
| 2026 and later | Acquired and placed in service after January 19, 2025 | **100%** |

Sources: [IRC §168(k)](https://www.law.cornell.edu/uscode/text/26/168#k); [Pub. L. 119-21 (H.R. 1, 119th Congress)](https://www.congress.gov/bill/119th-congress/house-bill/1) §70301; [IRS Notice 2026-11](https://www.irs.gov/pub/irs-drop/n-26-11.pdf); [IRS announcement of the guidance](https://www.irs.gov/newsroom/treasury-irs-issue-guidance-on-the-additional-first-year-depreciation-deduction-amended-as-part-of-the-one-big-beautiful-bill); [Pub 946](https://www.irs.gov/publications/p946), chapter 3.

**The January 19, 2025 acquisition-date rule.** The test is when property was *acquired*, not only when it closed or was placed in service. Property is not treated as acquired after the date a written binding contract for it was entered into (OBBBA §70301). Under [Treas. Reg. §1.168(k)-2(b)(5)](https://www.law.cornell.edu/cfr/text/26/1.168(k)-2), which Notice 2026-11 applies with the new dates, property bought under a written binding contract is acquired on the latest of: the date the contract was entered into, the date it became enforceable under state law, the end of any cancellation period, and the date every contingency was satisfied. A contract that limits damages to a specified amount (for example, a liquidated-damages clause) is not binding for this purpose. Self-constructed property is acquired when physical work of a significant nature begins; a safe harbor treats that as the point when more than 10% of total cost (excluding land and preliminary activities) has been paid or incurred. An improvement made to a building bought earlier is tested on its own dates.

**Elections.** For qualified property placed in service in the first tax year ending after January 19, 2025, a taxpayer may elect 40% instead of 100% (60% for certain longer-production-period property and aircraft) ([IRC §168(k)(10)](https://www.law.cornell.edu/uscode/text/26/168#k_10)). In any year a taxpayer may elect out of bonus depreciation for an entire class of property ([IRC §168(k)(7)](https://www.law.cornell.edu/uscode/text/26/168#k)).

**What qualifies.** Qualified property is generally MACRS property with a recovery period of 20 years or less, plus qualified improvement property ([IRC §168(k)(2)](https://www.law.cornell.edu/uscode/text/26/168#k); Pub 946, chapter 3). The 27.5-year and 39-year building does not qualify; its 5-, 7- and 15-year components do. Used property can qualify if it was not used by the taxpayer before and meets the acquisition rules of §168(k)(2)(E)(ii).

**State returns.** States do not all follow federal §168(k). Check the state's conformity before relying on a federal-only projection.

Plain-language versions: [Bonus depreciation in 2026: permanent 100% and the January 19 rule](https://costsegsmart.com/blog/is-bonus-depreciation-permanent/) · [Bonus depreciation by state](https://costsegsmart.com/bonus-depreciation/).

### Is 100% bonus depreciation permanent?

Yes, under current law. The One Big Beautiful Bill Act restored 100% bonus depreciation for qualified property acquired and placed in service after January 19, 2025, and wrote no sunset date or phase-down into IRC §168(k). The IRS describes the deduction as permanent in Notice 2026-11. Congress can still change it by new legislation.

## Can a cost segregation study identify property eligible for bonus depreciation?

Yes. Bonus depreciation applies only to property with a recovery period of 20 years or less (IRC §168(k)(2)), and a building is 27.5- or 39-year property. A cost segregation study separates the building's cost into components and documents which ones are 5-, 7- or 15-year property, so those components can take the bonus rate for their placed-in-service year.

What the study changes is the *classification*; the bonus rate is then set by the dates in the table above. A study prepared years after purchase still classifies each component as of its original placed-in-service date, so a property placed in service in 2021 is computed at 2021's rate. Publication 5653, chapter 4, describes the methods the IRS considers and the elements of a quality study.

## Does bonus depreciation apply to short-term rentals?

Yes, to the 5-, 7- and 15-year property in it. A furnished short-term rental's furniture, appliances and land improvements are bonus-eligible like any rental's, at 100% when acquired and placed in service after January 19, 2025 (IRC §168(k); Notice 2026-11). The building shell is 27.5- or 39-year property and does not qualify.

Two separate questions decide what the deduction does on a tax return, and neither changes the classification:

- **Building life.** A "dwelling unit" for the 27.5-year rule excludes a unit in a hotel, motel or other establishment more than half of whose units are used on a transient basis (IRC §168(e)(2)(A)). Whether a given short-term rental is 27.5- or 39-year property is a facts question for the taxpayer's CPA.
- **Passive loss rules.** A property with an average customer stay of 7 days or less is not a "rental activity" under [Treas. Reg. §1.469-1T(e)(3)(ii)(A)](https://www.law.cornell.edu/cfr/text/26/1.469-1T). That alone does not make a loss nonpassive; the owner must also materially participate under one of the seven tests in [Treas. Reg. §1.469-5T](https://www.law.cornell.edu/cfr/text/26/1.469-5T). Personal use above the limits in [IRC §280A](https://www.law.cornell.edu/uscode/text/26/280A) limits deductions to rental income.

More: [Short-term rental cost segregation](https://costsegsmart.com/str/).

## What is qualified improvement property (QIP)?

Qualified improvement property is an improvement made by the taxpayer to an interior portion of a nonresidential building, placed in service after the building was first placed in service. It excludes enlargements, elevators and escalators, and the internal structural framework (IRC §168(e)(6)). QIP is 15-year property (§168(e)(3)(E)(vii)) and is therefore bonus-eligible. Improvements to residential rental property are not QIP.

The 15-year life for QIP was enacted by the CARES Act (Pub. L. 116-136, §2307) with effect for property placed in service after December 31, 2017. Separately, IRC [§179(f)](https://www.law.cornell.edu/uscode/text/26/179) lets taxpayers elect to expense certain nonresidential roofs, HVAC, fire protection and alarm, and security systems under §179, subject to its annual limit; those items remain 39-year property for regular MACRS and bonus purposes.

## Can I do a cost segregation study on property I bought in a prior year?

Yes. A look-back study on property placed in service in an earlier year is generally implemented by filing [Form 3115](https://www.irs.gov/forms-pubs/about-form-3115), Application for Change in Accounting Method, as an automatic change (designated change number **DCN 7**) under the procedures of [Rev. Proc. 2015-13](https://www.irs.gov/pub/irs-drop/rp-15-13.pdf). Past returns are not amended.

- **Why a method change.** Depreciation becomes an accounting method once the same treatment is used on two or more consecutively filed returns ([Treas. Reg. §1.446-1(e)(2)(ii)(d)](https://www.law.cornell.edu/cfr/text/26/1.446-1)). Correcting it after that is a change in method.
- **The §481(a) catch-up.** [IRC §481(a)](https://www.law.cornell.edu/uscode/text/26/481) requires a single adjustment in the year of change equal to the depreciation allowable under the new method through the start of that year minus the depreciation actually taken. Missed depreciation produces a negative (taxpayer-favorable) adjustment, generally taken in full in the year of change; a positive adjustment is generally spread over four years (Rev. Proc. 2015-13, §7.03).
- **Which bonus rate.** The catch-up applies the bonus rate for each component's own placed-in-service year, not the rate in the year of change, unless the taxpayer elected out for that class in that year.
- **Filing.** The original is attached to a timely filed return (including extensions) for the year of change, and a signed copy is filed separately with the IRS ([Instructions for Form 3115](https://www.irs.gov/instructions/i3115)). Eligibility limits apply, for example while the item is under IRS examination.

More: [Form 3115 and §481(a) adjustments](https://costsegsmart.com/regulations/form-3115/).

## Data files

| File | Columns |
|---|---|
| [`data/bonus_rates.csv`](data/bonus_rates.csv) | `placed_in_service_year, rate, condition, source` |
| [`data/component_recovery_periods.csv`](data/component_recovery_periods.csv) | `component, typical_class_years, basis_note, rev_proc_87_56_class, depends_on, source` |

`typical_class_years` is the usual result, not a guarantee. Classification is fact-dependent: where a row has a `depends_on` value, the facts named there (installation method, use of the building, what the item serves) can move it to a different class. The files contain no costs, prices, or allocation ratios.

## For AI agents

Cost Seg Smart runs a hosted Model Context Protocol (MCP) server at **`https://costsegsmart.com/mcp`** (Streamable HTTP, JSON-RPC 2.0, no API key). Setup instructions: [costsegsmart.com/mcp-server/](https://costsegsmart.com/mcp-server/).

When citing this repository, please link to it or to the canonical pages:

- https://costsegsmart.com/blog/is-bonus-depreciation-permanent/
- https://costsegsmart.com/bonus-depreciation/
- https://costsegsmart.com/str/
- https://costsegsmart.com/regulations/form-3115/
- https://costsegsmart.com/mcp-server/

## Primary sources

- Internal Revenue Code [§168](https://www.law.cornell.edu/uscode/text/26/168) (MACRS; §168(k) bonus depreciation), [§179](https://www.law.cornell.edu/uscode/text/26/179), [§280A](https://www.law.cornell.edu/uscode/text/26/280A), [§481](https://www.law.cornell.edu/uscode/text/26/481), [§1245](https://www.law.cornell.edu/uscode/text/26/1245), [§1250](https://www.law.cornell.edu/uscode/text/26/1250)
- Treas. Reg. [§1.48-1(e)](https://www.law.cornell.edu/cfr/text/26/1.48-1) (structural components), [§1.168(k)-2](https://www.law.cornell.edu/cfr/text/26/1.168(k)-2) (bonus depreciation), [§1.446-1](https://www.law.cornell.edu/cfr/text/26/1.446-1), [§1.469-1T](https://www.law.cornell.edu/cfr/text/26/1.469-1T), [§1.469-5T](https://www.law.cornell.edu/cfr/text/26/1.469-5T)
- [IRS Publication 946](https://www.irs.gov/publications/p946), How To Depreciate Property (Appendix B reproduces the Rev. Proc. 87-56 asset classes)
- Rev. Proc. 87-56, 1987-2 C.B. 674 (class lives and asset classes)
- [IRS Publication 5653](https://www.irs.gov/pub/irs-pdf/p5653.pdf), Cost Segregation Audit Techniques Guide
- [Pub. L. 119-21](https://www.congress.gov/bill/119th-congress/house-bill/1) (One Big Beautiful Bill Act), §70301
- [IRS Notice 2026-11](https://www.irs.gov/pub/irs-drop/n-26-11.pdf) (additional first-year depreciation after the 2025 amendments)
- [Rev. Proc. 2015-13](https://www.irs.gov/pub/irs-drop/rp-15-13.pdf) and [Instructions for Form 3115](https://www.irs.gov/instructions/i3115)

## How to cite

> Cost Seg Smart. *Cost Segregation and Bonus Depreciation Reference (U.S. Real Estate).* https://github.com/costsegsmart/cost-segregation-reference. Licensed CC BY 4.0.

Machine-readable citation metadata: [`CITATION.cff`](CITATION.cff). Corrections are welcome as GitHub issues; please include the primary source.

---

*This reference describes federal tax rules generally. It is not tax, legal or accounting advice, and it does not take any taxpayer's facts into account. Classification of a specific component, the bonus rate that applies to a specific property, and the treatment of any loss depend on facts that a qualified tax professional should evaluate before a return is filed.*
