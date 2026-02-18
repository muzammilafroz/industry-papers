# Replication Guide for Selected Research Papers

> A comprehensive guide for replicating 34 research papers on Indian industrial economics, with special focus on replication feasibility using Indian datasets (ASI, NSSO, ASUSE, CMIE Prowess, NAS, and others).

---

## Paper 1: Foreign Direct Investment and R&D: Substitutes or Complements—A Case of Indian Manufacturing after 1991 Reforms

### 1. Citation
* **Authors:** Subash Sasidharan, Vinish Kathuria
* **Year:** 2011
* **Journal/Working Paper:** *World Development*, Vol. 39, No. 7, pp. 1226–1239
* **DOI/Link:** [10.1016/j.worlddev.2010.05.012](https://doi.org/10.1016/j.worlddev.2010.05.012)

### 2. Abstract (Concise Summary)
This study investigates whether foreign direct investment (FDI) inflows act as complements to or substitutes for indigenous R&D efforts of Indian manufacturing firms in the post-1991 liberalization era. Using an unbalanced panel of 1,843 firms over 1994–2005, the authors correct for self-selection bias (firms choosing whether or not to do R&D) through the Heckman two-step procedure. The full-sample analysis yields ambiguous results, but sub-sample analyses based on foreign-equity ownership and technology intensity reveal that FDI and R&D are complements when firms are classified by equity ownership. FDI induces R&D investment among foreign-owned firms in high-tech industries and among firms with minority foreign ownership.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | CMIE Prowess (firm-level balance sheet data); Secretariat of Industrial Approvals (SIA) for industry-level FDI approvals |
| Time Period | 1994–2005 |
| Unit of Analysis | Firm (listed manufacturing firms) |
| Sample Size | Unbalanced panel of ~1,850 firms across 26 three-digit manufacturing industries; ~2,655 firm-year observations in main regressions |
| Key Variables | R&D intensity (R&D/Sales), R&D dummy, foreign equity share, FDI approvals (industry-level), export intensity, capital goods imports intensity, disembodied technology imports, raw material imports, vertical integration, HHI (market concentration), firm size (relative to median), age, location dummy |

### 4. Econometric Methodology
- **Model type:** Heckman two-step selection model (HECKIT)
- **Main estimating equations:**
  - *Selection equation (Probit):* DRD_it = α₀SIZE_it + α₁FE_it + α₂EXPINT_it + α₃IMPCG_it + α₄DISTECH_it + α₅IMPRM_it + α₆FDI_jt + α₇VI_it + α₈HHI_jt + α₉LOC_it + Industry Dummies + Time Dummies + u_it
  - *Outcome equation (OLS with IMR):* RDINT_it = β₀SIZE_it + β₁FE_it + β₂EXPINT_it + β₃IMPCG_it + β₄DISTECH_it + β₅IMPRM_it + β₆FDI_jt + β₇VI_it + β₈HHI_jt + λ(IMR) + Industry Dummies + Time Dummies + ε_it
- **Identification strategy:** The location dummy (industrial estate) is excluded from the outcome equation to achieve identification in the Heckman procedure. Bootstrapped standard errors (1,500 replications) correct for heteroskedasticity.
- **Key assumptions:** Joint normality of error terms in selection and outcome equations; location (industrial estate) affects R&D decision but not R&D intensity; FDI approvals proxy actual FDI inflows.

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| CMIE Prowess (firm-level) | CMIE Prowess / ProwessIQ (updated) | CMIE ProwessIQ (annual subscription); covers ~40,000+ firms now |
| SIA FDI approvals data | DIPP/DPIIT FDI statistics | Department for Promotion of Industry and Internal Trade (DPIIT) FDI factsheets; RBI FDI data |
| HHI (concentration) | CMIE industry data / ASI-based computation | CMIE Industry Outlook or compute from ASI unit-level data |

#### 5.2 Suggested Variable Mapping
- R&D intensity → R&D expenditure / Net Sales from ProwessIQ
- Foreign equity → Foreign promoter shareholding from ProwessIQ
- FDI inflows → Sector-wise FDI equity inflows from DPIIT (replace approvals with actual inflows for improved accuracy)
- Capital goods imports, disembodied tech imports, raw material imports → Available in ProwessIQ balance sheet data
- Location dummy → Firm registered address; may require manual classification of industrial estate status
- HHI → Compute from ASI or Prowess sales data at NIC 3-digit level

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain ProwessIQ firm-level panel data for manufacturing firms (e.g., 2010–2023). Obtain DPIIT sector-wise FDI inflows data.
2. **Data cleaning:** Drop firms with zero sales or negative value added; exclude industries with no foreign presence; exclude SSI-reserved sectors. Construct unbalanced panel.
3. **Variable construction:** Compute R&D intensity (R&D/Sales), R&D dummy, foreign equity share, export intensity, technology import variables, vertical integration (VA/Sales), HHI at NIC 3-digit level, firm size relative to industry median, firm age.
4. **Econometric estimation:** Run Heckman two-step model (Stata: `heckman` command) with bootstrapped standard errors. Estimate for full sample, then sub-samples by technology intensity (OECD classification) and foreign equity ownership (majority vs. minority).
5. **Robustness checks:** Test non-linear size effects (quadratic); compare with simple Probit-Tobit; check sensitivity to FDI measure (approvals vs. actual inflows); test alternative HHI definitions.

#### 5.4 Potential Challenges in Indian Replication
- ProwessIQ covers only listed/large firms; unlisted and small firms doing R&D are excluded.
- R&D reporting thresholds in Indian Company Act may still bias the sample; the selection correction addresses this partially.
- Concordance between DPIIT FDI sector classification and NIC codes requires manual matching.
- Location dummy (industrial estate) may be hard to construct from available databases.
- Post-2005 patent regime changes (product patents from 2005) may structurally alter FDI–R&D dynamics.

### 6. Replication Difficulty Level
**Moderate** — The methodology (Heckman two-step) is standard and implemented in all major econometric software. ProwessIQ data is accessible to academic institutions. The main challenge lies in constructing the FDI variable at the correct sectoral level and the industrial estate dummy.

### 7. Recommended for Student Replication?
**Yes** — This is a well-structured study with clearly specified models, accessible data, and widely used econometric methods; extending it to the post-2005 patent reform period would add genuine academic value.

---

## Paper 2: 'Atmanirbhar Bharat Abhiyan': A Smooth Drive to Self-reliance?

### 1. Citation
* **Authors:** Sakshi Aggarwal, Debashis Chakraborty, Ranajoy Bhattacharyya
* **Year:** 2023
* **Journal/Working Paper:** *Economic & Political Weekly*, Vol. LVIII, No. 16, pp. 40–47
* **DOI/Link:** Published in EPW, April 22, 2023

### 2. Abstract (Concise Summary)
This paper examines the determinants of domestic value added (DVA) content in India's manufacturing exports across 10 key industrial sectors over 2000–2018, in the context of the Atmanirbhar Bharat Abhiyan (self-reliance campaign). Using OECD Trade in Value Added (TiVA) data combined with ASI and DPIIT sources, the authors estimate a Cobb-Douglas type production function in a panel data framework. The empirical results from a GLS random effects model show that domestic capital, FDI, skilled labour, and raw materials positively influence DVA content, while unskilled labour has a negative effect. An interaction term between FDI and skill intensity is also positive and significant. The findings suggest that export-led and FDI-promotion policies alone will not achieve self-reliance without coordinated skill augmentation and technology transfer.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | OECD TiVA database (2021 edition); Annual Survey of Industries (ASI); DPIIT SIA Statistics (sector-wise FDI); ITC Trade Map |
| Time Period | 2000–2018 |
| Unit of Analysis | Industry-year (10 manufacturing sectors × 19 years) |
| Sample Size | 190 observations (10 sectors × 19 years) |
| Key Variables | DVA content of exports (dependent), domestic capital (KD), FDI (KF), skilled labour (LSK), unskilled labour (LUSK), raw materials (M), number of firms, RTA dummy, FDI×(skilled/unskilled ratio) interaction |

### 4. Econometric Methodology
- **Model type:** Panel data GLS (Random Effects) regression
- **Main estimating equation:**
  L(DVA)_it = α₀ + β₁L(KD)_it + β₂L(KF)_it + β₃L(LSK)_it + β₄L(LUSK)_it + β₅L(M)_it + β₆LFIRMS_it + β₇L(KF×(S/U))_it + β₈RTA_t + Year Dummies + Sector Dummies + ε_it
  (L denotes logarithmic transformation)
- **Identification strategy:** Hausman test selects Random Effects over Fixed Effects; Levin-Lin-Chu panel unit root tests confirm stationarity; 2SLS endogeneity test (Durbin/Wu-Hausman) confirms exogeneity of regressors. Breusch-Pagan test confirms no heteroskedasticity.
- **Key assumptions:** Cobb-Douglas production function with constant elasticities; exogeneity of capital and labour inputs; DVA content proxies for industrial competitiveness.

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| OECD TiVA (DVA content) | OECD TiVA (2023 edition, updated) | OECD STAN/TiVA database (freely accessible); data may now extend to 2020 |
| ASI (capital, labour, materials, firms) | ASI unit-level or published tables | MoSPI Annual Survey of Industries; available via ePCO portal or published summaries |
| DPIIT SIA Statistics (sector-wise FDI) | DPIIT FDI factsheets | Updated DPIIT annual reports and factsheets |
| ITC Trade Map (trade data) | UN COMTRADE / DGCIS data | ITC Trade Map (free access), or DGCIS India Trade Portal |

#### 5.2 Suggested Variable Mapping
- DVA content → Directly from OECD TiVA (updated edition)
- Domestic capital (KD) → Physical working capital from ASI at NIC 4-digit level
- FDI (KF) → Sector-wise approved FDI inflows from DPIIT
- Skilled/unskilled labour → Workers classified by ASI (supervisory/managerial vs. directly engaged workers)
- Materials → Total input value from ASI
- Number of firms → Number of factories from ASI

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Download TiVA 2023 data for India; obtain ASI published tables or unit-level data for NIC 4-digit industries; obtain DPIIT FDI data.
2. **Data cleaning:** Build concordance between OECD TiVA sector codes, HS trade codes, and NIC codes (authors' concordance methodology). Aggregate ASI data to match TiVA sectors.
3. **Variable construction:** Compute log-transformed variables; construct RTA dummy (1 from 2011 onwards); construct FDI×skill-intensity interaction term.
4. **Econometric estimation:** Run panel unit root tests (LLC); Hausman test for RE vs. FE; estimate GLS random effects model with year and sector dummies; test for endogeneity via 2SLS.
5. **Robustness checks:** Extend time period to 2020; try Fixed Effects; use alternative DVA measures; test with different sector groupings.

#### 5.4 Potential Challenges in Indian Replication
- Constructing the concordance between OECD TiVA, HS, and NIC classifications is labour-intensive and requires domain expertise.
- ASI data at detailed NIC levels may have gaps, especially for newer NIC revisions (2008 vs. 2004).
- Small panel (N=10, T=19) limits the power of panel unit root and other diagnostic tests.
- TiVA data availability beyond 2018 depends on OECD update cycles.

### 6. Replication Difficulty Level
**Moderate** — The econometric framework is straightforward (panel GLS), but the data construction—particularly the three-way concordance between classification systems—is the most time-consuming step.

### 7. Recommended for Student Replication?
**Yes** — The study is policy-relevant (Atmanirbhar Bharat), uses publicly available data, and the methodology is accessible; students should be prepared for significant data harmonization effort.

---

## Paper 3: Profitability in India's Organized Manufacturing Sector: The Role of Technology, Distribution and Demand

### 1. Citation
* **Authors:** Deepankar Basu, Debarshi Das
* **Year:** 2018 (published online April 2017)
* **Journal/Working Paper:** *Cambridge Journal of Economics*, Vol. 42, No. 1, pp. 137–153
* **DOI/Link:** [10.1093/cje/bew068](https://doi.org/10.1093/cje/bew068) | JSTOR Stable URL: https://www.jstor.org/stable/10.2307/26784208

### 2. Abstract (Concise Summary)
This paper analyses profitability trends in India's organized manufacturing sector from 1982–83 to 2012–13 using aggregate ASI data. The authors construct replacement cost capital stock estimates via the perpetual inventory method and decompose the rate of profit into three components—profit share (distribution), capacity utilization rate (aggregate demand), and capacity-capital ratio (technology)—following the Weisskopf (1979) framework. Over the full period, the profit rate grew at approximately 1% per annum, driven primarily by a rising profit share (regressive redistribution away from labour). Five shorter-run profitability regimes are identified, with technology and demand fluctuations being the primary drivers of short-run profitability changes.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Annual Survey of Industries (ASI) — published aggregate tables; WPI for machinery from Office of Economic Advisor; CPI for Industrial Workers and WPI for manufactured products from RBI Handbook of Statistics |
| Time Period | 1982–83 to 2012–13 (31 years) |
| Unit of Analysis | Aggregate organized manufacturing sector (annual time series) |
| Sample Size | 31 annual observations |
| Key Variables | Net value added (Y), replacement cost capital stock (K), wages of productive workers (WP), compensation of unproductive labour (WUNP), rent, interest payments, price indices (WPIMAC, CPIIW, WPIMFG), number of workers, supervisors & managers |

### 4. Econometric Methodology
- **Model type:** Profit rate decomposition analysis (accounting decomposition, not regression-based)
- **Main decomposition equation:**
  R = (Π/Y) × (Y/Z) × (Z/K)
  where R = rate of profit, Π = profit income, Y = net value added, Z = capacity output (HP-filtered trend of Y), K = replacement cost capital stock
  
  Growth rate decomposition: Ṙ = (W/Π)×[ẏr – ẇr – λ̇wy] + (Ẏ/Z) + [żr – k̇r – λ̇ky]
  
  This decomposes profit rate growth into contributions from: profit share changes (distribution), capacity utilization changes (demand), and capacity-capital ratio changes (technology).
- **Identification strategy:** Not applicable (accounting decomposition, not causal estimation). Three methods used for computing growth rates: CAGR (endpoint), arithmetic mean of year-on-year growth, and log-linear time trend regression.
- **Key assumptions:** Perpetual inventory method for capital stock; Hodrick-Prescott filter for capacity output; Marxist definition of profit (surplus value = NVA minus productive worker compensation).

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI aggregate time series | Updated ASI aggregate tables | MoSPI ASI website; e-Annual Survey of Industries data portal (data now available to 2021–22) |
| WPI for machinery | WPI for machinery & equipment | Office of the Economic Advisor, Ministry of Commerce |
| CPI for Industrial Workers | CPI-IW | Labour Bureau / RBI DBIE |
| WPI for manufactured products | WPI-Manufacturing | Office of the Economic Advisor / RBI DBIE |

#### 5.2 Suggested Variable Mapping
All variables map directly as the study already uses Indian ASI data. For extension:
- Net value added → ASI Table: "Principal characteristics" at aggregate manufacturing level
- Workers, supervisors, managers → ASI employment tables
- Wages, salaries, benefits → ASI emolument tables
- Net investment, historical cost capital stock → ASI investment tables
- Price indices → Updated from respective official sources (rebased to new base years)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Download ASI aggregate time series from MoSPI (1981–82 to latest available, now ~2021–22). Download updated WPI and CPI series from RBI DBIE.
2. **Data cleaning:** Reconcile any base-year changes in price indices; rebase all indices to a common base year (e.g., 2011–12). Handle any breaks in ASI series due to NIC revisions.
3. **Variable construction:** Compute replacement cost capital stock using perpetual inventory method (Equation A1 in paper). Compute three profit measures (Π1, Π2, Π3). Estimate capacity output via HP filter on net value added. Construct all decomposition components.
4. **Econometric estimation:** Compute growth rates (CAGR, arithmetic mean, regression) for profit rate and each component over identified sub-periods. Perform full decomposition as per Equation 11.
5. **Robustness checks:** Use alternative depreciation rates; test sensitivity to HP filter parameter (λ); compare with NAS capital stock estimates; extend to industry-level disaggregation.

#### 5.4 Potential Challenges in Indian Replication
- ASI series may have breaks due to changes in survey methodology or NIC revisions (1998, 2004, 2008).
- Perpetual inventory method requires an initial-year benchmark capital stock; the choice of initial year affects the entire series.
- Distinguishing productive from unproductive labour in ASI data requires assumptions about the supervisory/managerial category.
- Small sample size (31 observations for the original; ~40 if extended to 2021–22) limits the use of structural break tests.

### 6. Replication Difficulty Level
**Easy** — The methodology is accounting-based decomposition, not advanced econometrics. All data are publicly available from official Indian sources. The perpetual inventory computation requires careful implementation but is conceptually straightforward.

### 7. Recommended for Student Replication?
**Yes** — An excellent starting exercise for students interested in Marxist political economy and industrial analysis. Extending the series to 2021–22 (covering demonetization, GST, COVID-19) would yield highly publishable insights.

---

## Paper 4: A Comparative Study between Organised and Unorganised Manufacturing Sectors in India

### 1. Citation
* **Authors:** Ruchika Gupta, Sanjay
* **Year:** 2012
* **Journal/Working Paper:** *The Journal of Industrial Statistics*, Vol. 1, No. 2, pp. 222–240
* **DOI/Link:** Not available (published by CSO/MoSPI)

### 2. Abstract (Concise Summary)
This paper undertakes a descriptive comparative analysis between India's organized and unorganized manufacturing sectors using ASI 2004–05 data for the organized sector and NSS 62nd Round (2005–06) data for the unorganized sector. The comparison is performed for five industry groups (Wearing Apparel, Food Products, Furniture, Textiles, and Tobacco) along parameters such as industry size (workers per enterprise), workers' performance (GVA per worker, output per worker), industrial productivity (input-output ratio), wage rate, energy efficiency, and female participation ratio. Key findings include: industry size is much smaller in the unorganized sector; productivity (input-output ratio) is higher in the unorganized sector (likely due to service-based receipts); wages are substantially higher in the organized sector; and female participation is greater in the organized sector.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (all states except Arunachal Pradesh, Mizoram, Sikkim, and Lakshadweep) |
| Data Source | Annual Survey of Industries (ASI) 2004–05 for organized sector; NSS 62nd Round (July 2005–June 2006) for unorganized sector |
| Time Period | 2004–05 (ASI), 2005–06 (NSS 62nd Round) |
| Unit of Analysis | Industry division (NIC 2-digit) and industry class (NIC 4-digit) |
| Sample Size | Five industry divisions (NIC 15, 16, 17, 18, 36); organized sector data covers 136,353 factories; unorganized sector covers 17,070,820 enterprises |
| Key Variables | Number of enterprises, number of workers, GVA, input, output, emoluments, fuel consumption, female workers, male workers |

### 4. Econometric Methodology
- **Model type:** Purely descriptive/comparative analysis using ratio-based indicators
- **Main indicators computed:**
  - Industry Size = Workers / Enterprises
  - GVA per Worker = GVA / Workers
  - Output per Worker = Output / Workers
  - Input-Output Ratio = Input / Output
  - Wage Rate = Annual Emoluments / Hired Workers
  - Fuel Efficiency = Fuel Consumption / (Output × 100)
  - Female Participation Ratio = Female Hired Workers / Male Hired Workers × 1000
- **Identification strategy:** Not applicable (no causal inference attempted)
- **Key assumptions:** Comparability between ASI and NSS definitions of inputs, outputs, and workers; assumes that selected NIC 4-digit classes within organized sector are representative counterparts of the broad unorganized sector activities.

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI 2004–05 | Latest ASI unit-level data (2021–22) | MoSPI ePCO portal |
| NSS 62nd Round (Unorganized Manufacturing) | ASUSE 2022–23 or 2023–24 | MoSPI/NSSO ASUSE microdata |

#### 5.2 Suggested Variable Mapping
All variables (workers, GVA, input, output, emoluments, fuel, gender-wise employment) are directly available in both ASI and ASUSE datasets. The NIC classification may need concordance if comparing across NIC-2004, NIC-2008, and current NIC revisions.

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain latest ASI unit-level data and ASUSE microdata from MoSPI.
2. **Data cleaning:** Select comparable industry divisions; ensure consistent variable definitions across ASI and ASUSE; handle different reference periods.
3. **Variable construction:** Compute all six comparative ratios for selected industries from both datasets.
4. **Econometric estimation:** Present tabular comparisons; compute t-tests for mean differences where appropriate.
5. **Robustness checks:** Extend comparison to more industries; add temporal dimension using multiple ASI/ASUSE rounds; compute confidence intervals using survey weights.

#### 5.4 Potential Challenges in Indian Replication
- NSS unorganized sector surveys used different reference periods (last 30 days vs. annual accounting year for ASI), leading to comparability issues.
- NIC classification changes between 2004 and 2008 make temporal comparisons difficult.
- The ASUSE (successor to NSS enterprise surveys) may have different variable definitions than the older NSS rounds.
- Unorganized sector estimates are sample-based with associated sampling errors; ASI is near-census for large factories.

### 6. Replication Difficulty Level
**Easy** — The analysis is entirely descriptive, requiring only data tabulation and ratio computation. No advanced econometric techniques are involved.

### 7. Recommended for Student Replication?
**Yes** — This is an accessible first project for students learning to work with Indian industrial data. Updating to current ASI and ASUSE data would provide useful contemporary insights into the organized-unorganized divide.

---

## Paper 5: What Drives the ICT Adoption in Unorganized Firms in India: An Application of Ordinal Probit Models

### 1. Citation
* **Authors:** Soumen Ghosh
* **Year:** 2025
* **Journal/Working Paper:** *Economics Bulletin*, Volume 0, Issue 0, pp. 1544–1553
* **DOI/Link:** Submitted July 2, 2025; Published October 16, 2025

### 2. Abstract (Concise Summary)
This study identifies the key drivers of ICT adoption among India's unorganized sector enterprises across four major industries: Manufacturing, Hospitality, Wholesale & Retail, and Construction & Real Estate. Using microdata from the Annual Survey of Unincorporated Sector Enterprises (ASUSE 2023), an ordinal probit regression model is employed where ICT adoption is coded as a three-category ordinal variable (no adoption, partial adoption, full adoption). The findings show that educated owners, access to finance, larger firms, younger firms, and urban location are associated with higher ICT adoption. Aggregate-level factors such as state-wise innovation index and internet penetration also positively influence adoption, though digital literacy shows a negative effect for manufacturing, and internet penetration is negative for hospitality, suggesting sector-specific structural barriers.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (national coverage) |
| Data Source | Annual Survey of Unincorporated Sector Enterprises (ASUSE) 2023, collected by NSSO; supplemented with Rajya Sabha data on digital literacy and internet subscribers; India Innovation Index 2020 (NITI Aayog) |
| Time Period | 2023 (cross-section) |
| Unit of Analysis | Individual unincorporated enterprise |
| Sample Size | 537,199 total; Manufacturing: 127,202; Hospitality: 46,629; Wholesale & Retail: 167,184; Construction & Real Estate: 51,888 |
| Key Variables | ICT_ADOPT (ordinal: 0/1/2), EDUCATION (ordinal), GENDER (binary), SOCIAL_GRP (binary), FIRMSIZE (continuous), FIRMAGE (continuous), ENTP_TYPE (binary), LOCATION (binary), SECTOR (urban/rural), DIG_LIT (state-level), INT_PENT (state-level), INNOVATION (state-level index) |

### 4. Econometric Methodology
- **Model type:** Ordinal Probit Model (primary); Ordinal Logit Model (robustness check)
- **Main estimating equation:**
  M*_i = x'_i β + ε_i, where ε_i ~ N(0,1)
  y_i = j if γ_{j-1} < M*_i ≤ γ_j (j = 1, 2, 3)
  
  Parameters estimated via Maximum Likelihood Estimation (MLE). Marginal/covariate effects computed for both continuous and indicator variables.
- **Identification strategy:** Cross-sectional variation across enterprises and states; location restriction (γ₁ = 0) and scale restriction (σ² = 1) for model identification. Robustness confirmed via ordinal logit.
- **Key assumptions:** Proportional odds / parallel regression assumption (implicit in ordinal probit); IID and normally distributed errors; state-level variables exogenously determined.

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASUSE 2023 microdata | ASUSE 2023–24 (same or updated round) | MoSPI/NSSO microdata portal (unit-level data access) |
| Rajya Sabha data on digital literacy | Data.gov.in | Rajya Sabha unstarred questions; data.gov.in portal |
| India Innovation Index 2020 | India Innovation Index (latest edition) | NITI Aayog |
| Internet subscriber data | TRAI reports | TRAI quarterly/annual reports on internet subscribers |

#### 5.2 Suggested Variable Mapping
All variables map directly from the ASUSE microdata questionnaire:
- ICT adoption → Question on computer/internet usage in operations
- Owner characteristics → Owner education, gender, social group from household block
- Firm characteristics → Total workers, firm age, enterprise type (OAE/establishment), location
- State-level variables → Merge from external government data sources

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Request ASUSE 2023–24 unit-level microdata from MoSPI. Download state-level digital literacy, internet penetration, and innovation index data.
2. **Data cleaning:** Filter to four industries; construct ordinal dependent variable from ICT adoption question; clean and code individual-level and firm-level variables; merge state-level indicators.
3. **Variable construction:** Create education categories, gender dummies, social group classification; compute firm size and age; standardize state-level variables.
4. **Econometric estimation:** Run ordinal probit models separately for each industry (Stata: `oprobit`; R: `polr`). Compute average marginal effects. Run ordinal logit as robustness check.
5. **Robustness checks:** Test proportional odds assumption (Brant test); try generalized ordered logit; include additional controls (e.g., access to credit); test regional sub-samples.

#### 5.4 Potential Challenges in Indian Replication
- ASUSE microdata access may require formal application to MoSPI.
- State-level variables from Rajya Sabha questions may be difficult to locate and update; alternative sources (TRAI, data.gov.in) should be identified.
- ICT adoption is self-reported and may suffer from measurement error in unorganized enterprises.
- Cross-sectional design limits causal interpretation; endogeneity of firm size and ICT adoption cannot be fully addressed.

### 6. Replication Difficulty Level
**Easy to Moderate** — The ordinal probit model is standard and well-documented. Data access is the main hurdle; once obtained, the analysis is straightforward. The cross-sectional nature simplifies estimation.

### 7. Recommended for Student Replication?
**Yes** — A timely and policy-relevant study on digital adoption in the informal sector. Students can extend it by exploring heterogeneity across states, adding financial access variables, or comparing across ASUSE rounds.

---

## Paper 6: Assessing the Productivity–Investment Nexus in Informal Economy: Evidence from India

### 1. Citation
* **Authors:** Sonakhya Samaddar, Ujjaval Srivastava
* **Year:** 2025
* **Journal/Working Paper:** *Sarvekshana* (Journal of MoSPI/NSO), 118th–119th Issue (Final version received May 2025, accepted August 2025)
* **DOI/Link:** Not available (government publication)

### 2. Abstract (Concise Summary)
This paper examines the relationship between capital investment (measured by owned fixed assets per worker) and labour productivity (output per worker) in India's informal sector, using unit-level data from ASUSE 2023–24. The analysis covers manufacturing, trade, and services sectors, separately for Own Account Enterprises (OAEs) and Hired Worker Establishments (HWEs). A log-linear production function is estimated with controls for ICT adoption, loan availability, firm age, urban/rural location, and household-based operation. The results reveal a significant positive association between capital investment and productivity across all sectors, with stronger effects in manufacturing OAEs. ICT adoption and loan availability significantly enhance productivity, particularly for OAEs. For HWEs, emolument per worker (human capital investment) emerges as the primary productivity driver, while the capital–productivity link is weaker.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (national coverage, rural and urban) |
| Data Source | Annual Survey of Unincorporated Sector Enterprises (ASUSE) 2023–24, collected by NSO |
| Time Period | October 2023–September 2024 |
| Unit of Analysis | Individual unincorporated enterprise |
| Sample Size | 497,688 establishments total: Manufacturing OAE (96,258), Manufacturing HWE (30,911), Trade OAE (92,182), Trade HWE (31,298), Services OAE (175,794), Services HWE (50,155) |
| Key Variables | Output per worker (dependent), owned fixed assets per worker, ICT use (binary), firm age (>3 years binary), loan availability (binary), hired asset ratio, urban location (binary), household location (binary), emolument per worker (HWE only) |

### 4. Econometric Methodology
- **Model type:** Log-linear OLS regression (extended production function)
- **Main estimating equation:**
  ln(y_i) = α + Σ β_j ln(X_ij) + Σ γ_k W_ik + e_i
  
  where y_i = output per worker; X_ij = continuous variables (asset per worker, hired asset ratio, emolument per worker for HWE); W_ik = binary variables (ICT use, firm age, loan availability, urban, household location)
- **Identification strategy:** Cross-sectional OLS with diagnostic checks: multicollinearity (VIF < 5), heteroskedasticity (Breusch-Pagan test—insignificant), normality of residuals confirmed via residual plots. Separate models for OAE and HWE in each of three sectors.
- **Key assumptions:** Log-linear functional form; exogeneity of regressors (acknowledged as a limitation—cross-sectional data limits causal inference); no omitted variable bias (conditional on controls).

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASUSE 2023–24 microdata | Same dataset or subsequent ASUSE rounds | MoSPI/NSO ASUSE unit-level data |
| Earlier informal sector surveys | NSS 67th Round (2010–11), NSS 73rd Round (2015–16) | NSSO microdata catalogue |

#### 5.2 Suggested Variable Mapping
All variables are directly available in the ASUSE microdata:
- Output per worker → Total output / total workers (computed from enterprise schedule)
- Owned fixed assets per worker → Value of owned fixed assets / total workers
- ICT use → Binary from ICT adoption question
- Firm age → Years since establishment (available in ASUSE)
- Loan availability → Outstanding loan status
- Emolument per worker → Total emoluments / hired workers (HWE only)
- Location variables → Rural/urban indicator and within/outside household premises

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain ASUSE 2023–24 unit-level data from MoSPI (same data used by authors, who are NSO officials).
2. **Data cleaning:** Filter to operational, market-oriented establishments with at least one worker (OAE or HWE). Remove non-operational units. Sample: ~497,688 observations.
3. **Variable construction:** Compute output per worker, assets per worker, hired asset ratio, emolument per worker. Create binary indicators. Apply log transformations.
4. **Econometric estimation:** Run multicollinearity diagnostics (correlogram, VIF). Estimate 6 OLS models (3 sectors × 2 establishment types). Test heteroskedasticity (Breusch-Pagan). Examine residual normality.
5. **Robustness checks:** Use robust standard errors; try quantile regression to capture heterogeneous effects; use survey weights; try IV estimation with loan availability instruments; extend to sub-industry analysis.

#### 5.4 Potential Challenges in Indian Replication
- ASUSE microdata access requires formal application; the authors are NSO officials with direct access.
- ~99% of respondents provide oral estimates (last 30 days), not audited accounts—measurement error may be substantial.
- Cross-sectional design: simultaneity between capital investment and productivity cannot be resolved without panel data or valid instruments.
- Survey design effects (stratification, clustering) should be accounted for using appropriate survey weights, which the paper does not explicitly discuss.

### 6. Replication Difficulty Level
**Easy** — Standard OLS regression with log transformations. The main challenge is data access. Once data is obtained, the analysis can be replicated quickly in Stata, R, or Python.

### 7. Recommended for Student Replication?
**Yes** — This is an ideal study for students working on the informal sector. The methodology is accessible, the policy relevance is high (linking capital investment to informal sector productivity), and extending to panel analysis using multiple ASUSE rounds would add substantial value.

---

## Paper 7: Firm Size and Productivity in the Informal Sector: Evidence from India

### 1. Citation
* **Authors:** Lokesh Posti, Abhradeep Maiti
* **Year:** 2023
* **Journal/Working Paper:** *The Indian Economic Journal*, pp. 1–19 (Article first published online 2023)
* **DOI/Link:** [10.1177/00194662231202088](https://doi.org/10.1177/00194662231202088)

### 2. Abstract (Concise Summary)
This study examines the relationship between firm size and productivity in India's informal (unorganized) sector using a novel pseudo-panel data design. By combining three nationally representative NSSO cross-sectional surveys (55th Round: 1999–2000, 67th Round: 2010–11, 73rd Round: 2015–16), the authors construct 47,683 cohorts based on state, industry, location, ownership, and size quantiles. Total factor productivity (TFP) is estimated using the Wooldridge-modified Olley-Pakes semi-parametric method. Random effects and dynamic panel specifications reveal a strong positive relationship between firm size (employment-based) and TFP across all major industries. However, the analysis also shows that while GVA rises with firm size, average wages remain stagnant—indicating capital accumulation at the expense of labour exploitation. The findings support a "carrot-and-stick" approach to gradual formalization.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (national coverage) |
| Data Source | NSSO 55th Round (1999–2000), 67th Round (2010–11), 73rd Round (2015–16) — all on unincorporated non-agricultural enterprises |
| Time Period | 1999–2000 to 2015–2016 |
| Unit of Analysis | Pseudo-panel cohort (group of homogenous firms) for main analysis; individual firm for supplementary analysis (73rd Round) |
| Sample Size | 820,485 individual observations pooled; 47,683 cohorts constructed; 171,956 firms from 73rd Round for supplementary analysis |
| Key Variables | TFP (Wooldridge-Olley-Pakes), firm employment size (categorical: Small ≤2, Mid 3–4, Big ≥5), firm asset size (categorical), total receipts, hired capital, owned capital, investment, market concentration (HHI at state-industry level), formal loan dummy, informal loan dummy, GVA, average wage (emoluments/workers), firm age, caste of owner |

### 4. Econometric Methodology
- **Model type:** (1) Random Effects panel regression on pseudo-panel; (2) Dynamic panel model (lagged dependent variable); (3) Cross-sectional OLS for GVA and wage analysis
- **Main estimating equations:**
  - Static RE: log(TFP)_ct = β₀ + β₁FirmSize_ct + β₂Z_ct + δ_c + η_t + ε_ct
  - Dynamic: log(TFP)_ct = β₀ + ρlog(TFP)_{c,t-1} + β₁FirmSize_ct + β₂Z_ct + δ_c + η_t + ε_ct
  - GVA equation: log(GVA)_i = α₀ + α₁log(TotalWorkers)_i + α₂log(Capital)_i + X_iδ + η_i
  - Wage equation: log(AvgWage)_i = β₀ + β₁log(GVA)_i + β₂log(TotalWorkers)_i + β₃log(Capital)_i + X_iγ + μ_i
- **TFP estimation:** Cobb-Douglas production function estimated via Wooldridge-modified Olley-Pakes semi-parametric method (using investment as proxy for unobserved productivity shock), implemented via GMM (Stata package `prodest`).
- **Identification strategy:** Pseudo-panel construction addresses lack of true panel data; cohort fixed effects control for time-invariant unobserved heterogeneity; dynamic specification checks for TFP persistence and potential endogeneity; HHI computed at state-industry level to proxy market competition.
- **Key assumptions:** Cohort means approximate population means (requires sufficiently large cohort sizes); RE assumption that unobserved cohort effects are uncorrelated with firm size; Olley-Pakes monotonicity condition (investment is monotonically increasing in productivity).

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| NSS 55th Round (1999–2000) | Same dataset | NSSO microdata catalogue (microdata.gov.in) |
| NSS 67th Round (2010–11) | Same dataset | NSSO microdata catalogue |
| NSS 73rd Round (2015–16) | Same dataset | NSSO microdata catalogue |
| For extension: ASUSE 2022–23, 2023–24 | ASUSE microdata | MoSPI/NSO |

#### 5.2 Suggested Variable Mapping
- Total receipts → Total revenue/receipts from enterprise schedule
- Capital (hired and owned) → Fixed assets (hired and owned) from asset block
- Investment → Additions to fixed assets during reference period
- Total workers → All persons engaged (working owners + hired + family workers)
- Emoluments → Total compensation paid to hired workers
- Firm age, caste, location → Available in all NSSO enterprise survey schedules
- HHI → Computed from total receipts at NIC 2-digit × state level

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Download unit-level microdata for NSS 55th, 67th, and 73rd Rounds from the NSSO microdata portal. For extension, also obtain ASUSE 2022–23 or 2023–24 data.
2. **Data cleaning:** Harmonize variable definitions across rounds (variable names differ); deflate monetary variables using WPI (manufacturing) and CPI (services) to common base year (2010); retain only common variables across all three rounds.
3. **Variable construction:** Estimate TFP using `prodest` Stata package (Wooldridge-Olley-Pakes method). Construct pseudo-panel cohorts using seven classification criteria (state, industry, location, nature of operation, employment quantile, capital quantile, ownership type). Compute cohort means. Compute HHI at state-industry level.
4. **Econometric estimation:** Run Random Effects regression (Equation 2.1) and dynamic panel (Equation 2.2) on pseudo-panel. For supplementary analysis (73rd Round only), estimate GVA and wage equations (Equations 4 and 5) via OLS with fixed effects for industry, state, location, and nature of operation.
5. **Robustness checks:** Use alternative firm size measures (asset-based); use alternative performance measures (GVA, revenue); test with Arellano-Bond GMM for dynamic panel; include additional ASUSE round for extended panel.

#### 5.4 Potential Challenges in Indian Replication
- Pseudo-panel methodology involves judgment calls in cohort construction; results may be sensitive to cohort granularity.
- Common variables across the three NSSO rounds are limited, restricting the set of controls.
- The Olley-Pakes method requires non-zero investment for the proxy to work; many informal firms may report zero investment.
- NSS 55th Round has the fewest variables, constraining the analysis.
- Measurement error in cohort means (information loss from aggregation).
- Dynamic panel estimation on pseudo-panels requires careful treatment of cohort attrition and unbalancedness.

### 6. Replication Difficulty Level
**Hard** — The study involves multiple advanced techniques: semi-parametric TFP estimation (Olley-Pakes), pseudo-panel construction from repeated cross-sections, and dynamic panel estimation. Harmonizing three different NSSO rounds adds substantial data preparation burden.

### 7. Recommended for Student Replication?
**With caution** — This is suitable for advanced M.Phil/Ph.D. students with experience in panel data methods and familiarity with NSSO microdata. The pseudo-panel construction and TFP estimation require careful implementation, but the study offers a rich methodological learning experience.

---
---

## Paper 8: Foreign Direct Investment and Growth: Does the Sector Matter?

### 1. Citation
* Authors: Laura Alfaro
* Year: 2003
* Journal/Working Paper: Harvard Business School Working Paper (later published in various forms)
* DOI/Link: Not specified in manuscript; contact: lalfaro@hbs.edu

### 2. Abstract (Concise Summary)
This paper investigates whether the growth effects of foreign direct investment (FDI) differ across economic sectors—primary, manufacturing, and services. Using cross-country data for 47 countries over 1981–1999, the study finds that aggregate FDI has an ambiguous effect on economic growth. However, when disaggregated by sector, FDI in the primary sector tends to have a negative effect on growth, FDI in manufacturing exerts a positive and significant effect, and evidence for the services sector remains inconclusive. The results are robust to controls for human capital, financial development, institutional quality, and lagged FDI values.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | 47 countries worldwide (OECD and developing) |
| Data Source | OECD International Direct Investment Statistics; UNCTAD World Investment Directory (1993, 2000 editions); Penn World Tables; World Development Indicators; ICRG |
| Time Period | 1981–1999 (cross-sectional averages) |
| Unit of Analysis | Country |
| Sample Size | 47 countries; reduced to 30 in lagged-FDI robustness checks |
| Key Variables | Per capita GDP growth rate; FDI/GDP by sector (primary, manufacturing, services); initial GDP per capita; human capital (years of secondary schooling); inflation; government spending; private credit/GDP; institutional quality (ICRG); domestic investment; openness |

### 4. Econometric Methodology
- **Model type:** Cross-section OLS regressions with White's heteroskedasticity-corrected standard errors
- **Main estimating equation:**
  - Baseline: GROWTH_i = β₀ + β₁·INITIAL_GDP_i + β₂·CONTROLS_i + β₃·FDI_i + ν_i
  - Sectoral: GROWTH_i = β₀ + β₁·INITIAL_GDP_i + β₂·CONTROLS_i + β₃·FDI^P_i + β₄·FDI^M_i + β₅·FDI^S_i + ν_i
  - Where P = primary, M = manufacturing, S = services
- **Identification strategy:** Cross-country growth regressions following Borensztein et al. (1998) framework; robustness via lagged FDI to address endogeneity, exclusion of outlier countries, interaction with human capital
- **Key assumptions:** Cross-sectional variation captures long-run relationships; sector-level FDI shares proxy for intensity of foreign presence; lagged FDI serves as valid instrument for current FDI

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| Cross-country FDI by sector | State-level or industry-level FDI inflows by sector | RBI data on FDI inflows by sector; DIPP (now DPIIT) FDI statistics |
| GDP growth rates | State-level GSDP growth | CSO/MOSPI State Domestic Product series |
| Human capital | State-level education indicators | NSS Education Rounds; ASER; Census literacy rates |
| Financial development | State-level bank credit/GSDP | RBI Basic Statistical Returns of Scheduled Commercial Banks |
| Institutional quality | State-level governance indices | India State-level governance indicators; NITI Aayog indices |

#### 5.2 Suggested Variable Mapping
- Cross-country GDP growth → State-level real per capita GSDP growth
- Sectoral FDI/GDP → Sectoral FDI inflows/GSDP at state level
- Human capital → Average years of schooling or literacy rate by state
- Private credit → Bank credit to private sector / GSDP
- Institutional quality → State governance/ease of doing business rankings

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain state-level FDI inflows by sector from DPIIT/RBI; GSDP series from MOSPI; banking data from RBI; education data from Census/NSS
2. **Data cleaning:** Construct state-year panel or cross-sectional averages; concordance of FDI sector classifications to NIC codes; deflate monetary variables
3. **Variable construction:** Compute FDI/GSDP ratios by sector; construct control variables (initial GSDP per capita, credit/GSDP, human capital measures, infrastructure proxies)
4. **Econometric estimation:** Run OLS cross-section or panel regressions of GSDP growth on sectoral FDI shares with controls; apply White's robust standard errors; test with lagged FDI
5. **Robustness checks:** Exclude outlier states; interact FDI with human capital; use GMM panel estimators if time dimension allows; test sub-period stability

#### 5.4 Potential Challenges in Indian Replication
- State-level FDI data by sector is less readily available compared to national aggregates
- FDI is often recorded at the approval/route level rather than actual disbursement level
- State-level GSDP methodology changes (base year revisions) require careful deflation
- Endogeneity more pronounced at sub-national level since FDI gravitates toward fast-growing states
- Limited time variation if using cross-sectional framework

### 6. Replication Difficulty Level
**Moderate** – The cross-section OLS methodology is straightforward, but obtaining consistent state-level sectoral FDI data over a long period is the main challenge.

### 7. Recommended for Student Replication?
**With caution** – Feasible as a learning exercise if students focus on a panel of Indian states and accept available (possibly imperfect) FDI disaggregation data.

---

## Paper 9: Impact of Trade Liberalization on Foreign Direct Investment in Indian Industries

### 1. Citation
* Authors: Bishwanath Goldar and Rashmi Banga
* Year: 2007
* Journal/Working Paper: ARTNeT Working Paper Series, No. 36, Asia-Pacific Research and Training Network on Trade (ARTNeT), Bangkok
* DOI/Link: https://hdl.handle.net/10419/178394

### 2. Abstract (Concise Summary)
This paper examines how trade liberalization in India during the 1990s influenced FDI inflows into manufacturing industries. Analyzing the channels through which different types of trade—particularly materials import intensity (reflecting cross-border vertical integration) and intra-industry trade—affect FDI, the authors employ three levels of analysis: (i) a panel data model for 78 three-digit industries over 1991–92 to 1997–98, (ii) an inter-firm cross-sectional analysis, and (iii) an inter-state analysis. Results indicate that tariff reductions increased materials import intensity and intra-industry trade; the former had a favourable effect on FDI inflows, while horizontal intra-industry trade did not significantly boost FDI. Trade associated with cross-border vertical integration is found to be the more important channel.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Annual Survey of Industries (ASI), CSO; Prowess database (CMIE); World Bank Trade and Production Database (for IIT computation); tariff and NTB data from Goldar & Aggarwal (2005) |
| Time Period | 1991–92 to 1997–98 |
| Unit of Analysis | Industry (78 three-digit NIC industries); firm (cross-sectional); state (inter-state analysis) |
| Sample Size | 78 industries × 7 years = ~546 observations (panel); firm-level cross-section; state-level cross-section |
| Key Variables | Foreign companies' share in industry sales (FDI indicator); materials import intensity; Grubel-Lloyd intra-industry trade index; tariff rates; non-tariff barriers (import coverage ratio); R&D intensity; technology import intensity; capital goods import intensity; export intensity; industry output; capital-labour ratio; wage share |

### 4. Econometric Methodology
- **Model type:** Panel data regressions (fixed effects and random effects); Hausman test for model selection; inter-firm and inter-state OLS cross-sections
- **Main estimating equations:**
  - FDI share = f(materials import intensity, IIT index, technology import intensity, R&D intensity, capital goods import intensity, output, K/L ratio, wage share)
  - Materials import intensity = f(tariff rate, NTB, R&D, capital goods imports, output, K/L, wage share, export intensity)
  - IIT = f(tariff rate, NTB, R&D, capital goods imports, output, K/L, wage share)
- **Identification strategy:** Two-stage analytical chain: (1) trade liberalization → trade flows, (2) trade flows → FDI; panel structure exploits within-industry variation; Hausman test determines FE vs RE
- **Key assumptions:** Tariff and NTB reductions are exogenous policy shocks; foreign share in sales adequately proxies FDI intensity; industry-level concordance between Prowess and ASI is reliable

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI industry data | ASI (updated rounds) | MOSPI Annual Survey of Industries (unit-level data available until latest rounds) |
| Prowess (CMIE) | Prowess IQ / ProwessIQ | CMIE Prowess IQ (subscription-based) |
| Trade data (4-digit ISIC) | India trade data at HS/ISIC level | WITS/UN Comtrade; DGCIS India trade data |
| Tariff and NTB data | Updated tariff series | WTO Tariff Download Facility; TRAINS database; DGFT notifications |

#### 5.2 Suggested Variable Mapping
- Foreign companies' share → Use Prowess equity data (>10% foreign equity threshold) matched to NIC-classified industries
- Grubel-Lloyd IIT index → Compute from HS-level trade data mapped to NIC industries
- Materials import intensity → Raw materials imports / total sales from ASI or Prowess
- Tariff and NTB → Construct from TRAINS database or Ministry of Commerce tariff schedules

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain unit-level ASI data for post-2000 period; access Prowess IQ; download trade data from WITS; obtain tariff schedules
2. **Data cleaning:** Build concordance between Prowess industry codes and NIC 3-digit codes; match trade data (HS codes) to NIC; construct balanced panel
3. **Variable construction:** Compute FDI share, materials import intensity, IIT index, tariff rates, R&D intensity, technology import intensity, export intensity per industry-year
4. **Econometric estimation:** Estimate FE and RE panel models with Hausman tests; estimate two-equation system linking trade liberalization to trade flows and trade flows to FDI
5. **Robustness checks:** Remove outlier industries (high foreign share >45%); extend to post-1998 period with updated NIC concordance; test with GMM or IV methods

#### 5.4 Potential Challenges in Indian Replication
- NIC classification changes (1987, 1998, 2004, 2008) necessitate careful concordance for post-1998 panels
- Prowess database access requires paid subscription
- Defining "foreign firms" consistently over time (threshold changes)
- IIT computation requires accurate concordance between trade classifications and industrial classifications
- The original analysis was restricted to pre-1998 due to NIC changes

### 6. Replication Difficulty Level
**Moderate** – The econometric techniques (FE/RE panel) are standard, but data concordance across classifications and sourcing proprietary Prowess data add complexity.

### 7. Recommended for Student Replication?
**Yes** – An excellent exercise for understanding trade-FDI linkages in India; updating the analysis to more recent periods would add significant value.

---

## Paper 10: How Diversified is the Informal Manufacturing Sector Across Indian States?

### 1. Citation
* Authors: Dilip Saikia
* Year: 2017
* Journal/Working Paper: Journal of Rural and Industrial Development, Volume 5, Issue 2, October 2017
* DOI/Link: Not specified; author contact: dilip.gu@gmail.com

### 2. Abstract (Concise Summary)
This paper examines the structural base and degree of diversification of India's informal (unorganised) manufacturing sector across states. Using data from NSSO quinquennial rounds on unorganised manufacturing enterprises for 1994–95, 2005–06, and 2010–11, the study employs location quotients to identify the industrial base of each state and a diversification coefficient to measure the extent of industrial diversity at the two-digit industry level. The analysis also examines co-location patterns of informal manufacturing enterprises. Results show that most Indian states have a narrow industrial base, diversification is limited, and there is a significant positive correlation between diversification of the informal manufacturing sector and the level of industrial development.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (state-level, 27 states/UTs) |
| Data Source | National Sample Survey (NSS) quinquennial rounds on Unorganised Manufacturing Enterprises: 51st round (1994–95), 62nd round (2005–06), 67th round (2010–11) |
| Time Period | 1994–95, 2005–06, 2010–11 |
| Unit of Analysis | State × two-digit industry group |
| Sample Size | 27 states across 14 two-digit NIC industry groups × 3 time points |
| Key Variables | Gross value added by industry and state; number of enterprises; employment; location quotients; diversification coefficients; share of manufacturing in NSDP; per capita unregistered manufacturing NSDP |

### 4. Econometric Methodology
- **Model type:** Descriptive statistical analysis using location quotients and diversification coefficients; rank correlation analysis
- **Main measures:**
  - Location Quotient: LQ_ik = (V_ik / V_k) / (V_i / V), where V = value added
  - Diversification Coefficient: DC_k = 1 − Σ|V_ik/V_k − V_i/V| (ranges from 0 to 1)
  - Co-location analysis: Pearson correlation coefficients between industry employment shares across states
- **Identification strategy:** Descriptive; no causal identification. Rank correlations test the association between diversification and level of industrialisation
- **Key assumptions:** Gross value added at two-digit NIC level adequately captures industrial structure; NSS sampling design provides representative state-level estimates; diversification coefficient captures relative diversity against the national benchmark

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| NSS 51st, 62nd, 67th rounds | NSS 73rd round (2015–16) and any newer NSSO/MoSPI enterprise surveys | MOSPI/NSSO unit-level data (available for download/purchase) |
| NSDP data | Updated state domestic product | MOSPI/RBI State Finances database |

#### 5.2 Suggested Variable Mapping
- Direct replication: all variables are directly available from NSS unorganised manufacturing enterprise surveys
- Update NIC codes to NIC 2008 for consistency with 73rd round data
- Use GVA at two-digit level for both location quotient and diversification coefficient computation

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain NSS unit-level data for 73rd round (2015–16) from MOSPI; download NSDP data from RBI/MOSPI
2. **Data cleaning:** Tabulate GVA, employment, and number of enterprises by state and two-digit NIC code; apply NSS sampling weights; handle new states (Telangana)
3. **Variable construction:** Compute location quotients for each state-industry pair; compute diversification coefficients for each state; compute correlation matrices for co-location analysis
4. **Econometric estimation:** Rank the states by diversification coefficient; compute Spearman rank correlations between diversification and industrialisation indicators; plot scatter diagrams
5. **Robustness checks:** Use alternative measures (number of enterprises, employment instead of GVA); test at three-digit NIC level; compare across rounds for trends

#### 5.4 Potential Challenges in Indian Replication
- NIC code changes between rounds require concordance (NIC 1998 vs NIC 2004 vs NIC 2008)
- NSS sampling weights must be correctly applied for state-level representativeness
- Creation of new states (Telangana from Andhra Pradesh in 2014) affects comparability
- Small sample sizes for northeastern states may affect reliability of location quotients

### 6. Replication Difficulty Level
**Easy** – The methodology is purely descriptive (location quotients, diversification coefficients, correlations); data is publicly available from NSSO.

### 7. Recommended for Student Replication?
**Yes** – Excellent introductory exercise for students learning to work with NSS enterprise-level data and descriptive industrial analysis.

---

## Paper 11: Long-run Performance of the Organised Manufacturing Sector in India: An Analysis of Sub-periods and Industry-level Trends

### 1. Citation
* Authors: Amit Basole and Amay Narayan
* Year: 2020
* Journal/Working Paper: Economic & Political Weekly (EPW), Vol. LV, No. 10, March 7, 2020
* DOI/Link: Not specified

### 2. Abstract (Concise Summary)
This paper traces the evolution of key parameters—employment, wages, capital intensity, and productivity—in India's organised manufacturing sector over a 34-year period (1983–2017) using ASI data at the 3-digit NIC level. Employing the Bai-Perron structural breakpoint test, the authors identify three statistically distinct sub-periods: 1988–96 (weak employment growth, rapid capital substitution, rising wages), 1996–2006 (employment decline, stagnant wages, growing productivity-wage divergence), and 2006–17 (strong employment and wage growth despite rising capital intensity). A shift-share decomposition reveals that the decline in the labour-to-capital ratio is predominantly driven by within-industry changes rather than compositional shifts across industries. The authors also construct an industry typology based on the capacity to deliver both employment and wage growth.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Annual Survey of Industries (ASI) concorded series from EPWRF India Time Series (EPWRFITS) database |
| Time Period | 1982–83 to 2016–17 (34 years) |
| Unit of Analysis | Industry (55 industries at 3-digit NIC level) |
| Sample Size | 55 industries × 34 years |
| Key Variables | Total persons engaged (employment); real wages and salaries (deflated by CPI-IW); real output and GVA (deflated by WPI-MP); real fixed capital stock (perpetual inventory method, deflated by WPI-MM); labour-capital ratio; labour productivity (GVA/worker); wage share (wages/GVA); employment elasticity |

### 4. Econometric Methodology
- **Model type:** Bai-Perron structural breakpoint tests; shift-share decomposition; industry fixed-effects panel regression
- **Main estimating equations:**
  - Shift-share decomposition: l_{t+1} − l_t = Σ l_it(s_{it+1} − s_it) + Σ (l_{it+1} − l_it)s_it + interaction term, where l = L/K, s_i = K_i/K
  - Wage share decomposition: (wL)/Y = (L/K) × (wL/L) × (K/Y); growth rate of wage share = sum of growth rates of three components
  - Employment elasticity (panel): log(L_it) = α_i + β·log(Y_it) + γ·log(K/L_it) + ε_it
  - Bai-Perron test: sequential testing of L+1 vs L breaks on log-linear time trend of aggregate employment and wages
- **Identification strategy:** Structural break analysis to endogenously determine sub-periods; descriptive decomposition to separate within vs. between industry effects
- **Key assumptions:** ASI concorded series are consistent over time; capital stock via perpetual inventory method is reliable; Bai-Perron test identifies genuine structural breaks rather than data artefacts

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI concorded series (EPWRFITS) | ASI unit-level data or EPWRFITS | EPWRF India Time Series (subscription); or raw ASI unit-level data from MOSPI |
| CPI-IW, WPI deflators | Same deflators (updated) | Labour Bureau (CPI-IW); Office of Economic Adviser (WPI) |

#### 5.2 Suggested Variable Mapping
- Direct replication: all variables are from ASI and publicly available deflator series
- Capital stock construction via perpetual inventory method following Balakrishnan and Pushpangadan (1994)
- Employment = total persons engaged; wages = total wages and salaries

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Subscribe to EPWRFITS for concorded ASI data at 3-digit NIC level; alternatively, obtain unit-level ASI from MOSPI and concord manually
2. **Data cleaning:** Exclude industries removed from ASI coverage post-1999 for consistency; construct concordance across NIC revisions (1987, 1998, 2004, 2008); deflate using CPI-IW and WPI
3. **Variable construction:** Compute real capital stock (perpetual inventory method); compute L/K ratio, labour productivity, wage share, employment elasticity per industry-year
4. **Econometric estimation:** Apply Bai-Perron structural break test (using EViews or R strucchange package) to aggregate employment and wage series; conduct shift-share decomposition of L/K ratio; run panel FE regression of employment on output and capital intensity
5. **Robustness checks:** Use production workers vs. total persons engaged; use GVA vs. gross output; test with different deflators; extend series beyond 2017 if data available

#### 5.4 Potential Challenges in Indian Replication
- EPWRFITS database requires institutional subscription
- Constructing capital stock via perpetual inventory method requires careful assumptions about depreciation rates and initial capital stock
- NIC concordance across multiple revisions is labour-intensive
- Bai-Perron test requires appropriate trimming parameters and HAC standard error specification

### 6. Replication Difficulty Level
**Moderate** – The econometric methods (Bai-Perron, shift-share) require some sophistication, and constructing the concorded time series is the most time-consuming part.

### 7. Recommended for Student Replication?
**Yes** – An outstanding exercise for students interested in Indian manufacturing trends; the methods are well-documented and reproducible with EPWRFITS data.

---

## Paper 12: Product Scope and Productivity: Evidence from India's Product Reservation Policy

### 1. Citation
* Authors: Ishani Tewari and Joshua Wilde
* Year: 2019
* Journal/Working Paper: Southern Economic Journal, 86(1), 339–362
* DOI/Link: https://doi.org/10.1002/soej.12368

### 2. Abstract (Concise Summary)
This paper examines how India's product reservation policy—which reserved certain products for exclusive manufacture by small-scale enterprises—affected firm size, productivity, product churning, and industry dynamics. Leveraging quasi-exogenous variation in the timing of dereservation of over 800 products between 1997 and 2010, the authors employ a difference-in-differences framework using firm-level ASI data from 2000 to 2010. They find that dereservation increased firm size and productivity by 1–4%, driven primarily by multiproduct firms entering previously restricted product spaces. Firms responded by adding formerly reserved products while shedding less profitable unreserved products, leading to a net reduction in product scope accompanied by TFP gains. The findings underscore the importance of intra-firm heterogeneity in assessing size-contingent regulations.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Annual Survey of Industries (ASI), unit-level panel data; Ministry of Small Scale Industries (dereservation schedules and ASICC product codes) |
| Time Period | 2000–2010 (ASI financial years) |
| Unit of Analysis | Factory/plant (establishment level) |
| Sample Size | ~326,295 plant-year observations; ~114,245 observations in falsification tests |
| Key Variables | Log gross value added (GVA); log employment; log capital; TFP (Levinsohn-Petrin method); number of products produced; number of reserved/unreserved products; fraction of output unreserved in 3-digit industry (main independent variable); multiproduct firm dummy; unreserved firm dummy |

### 4. Econometric Methodology
- **Model type:** Difference-in-differences (DID) with firm and year fixed effects
- **Main estimating equation:**
  - Y_ist = α_i + γ_t + β·D_{s,t−1} + ε_ist
  - Where Y_ist = outcome (log GVA, log employment, log capital, log TFP, number of products) for firm i in industry s at time t
  - D_{s,t−1} = fraction of output in industry s that is unreserved (lagged one year)
  - α_i = firm fixed effects; γ_t = year fixed effects
  - Augmented specification includes interactions with multiproduct dummy and unreserved firm dummy (triple interactions)
- **Identification strategy:** Exploits plausibly exogenous variation in the timing and intensity of product dereservation across industries; base-year (2000) product output shares used to construct treatment intensity to avoid endogeneity; parallel trends assumption tested via pre-treatment falsification regressions
- **Key assumptions:** Timing of dereservation is quasi-random (not correlated with pre-existing industry trends); firm FE controls for time-invariant unobservables; base-year output shares prevent endogenous treatment variable construction
- **TFP estimation:** Levinsohn and Petrin (2003) method using material inputs as proxy for unobserved productivity at 3-digit industry level

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI unit-level panel (2000–2010) | ASI unit-level data (extended to 2018 or later) | MOSPI ASI unit-level data with panel identifiers |
| Dereservation schedules | Same government notifications | Ministry of MSME official gazette notifications; DCMSME website |
| ASICC product codes | ASICC / NPCMS concordance | ASI product-level data; official concordance tables |

#### 5.2 Suggested Variable Mapping
- Direct replication: all variables come from ASI unit-level data
- TFP: estimate using Levinsohn-Petrin (2003) at 3-digit NIC level using material inputs as proxy
- Treatment variable: fraction of output unreserved, constructed from base-year product output shares and dereservation notification dates
- Deflators: WPI for output and capital (from Handbook of Industrial Statistics)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain ASI unit-level data with panel identifiers (2000–2010 or extended); download dereservation notification schedules from MSME Ministry; obtain ASICC-NIC concordance
2. **Data cleaning:** Construct firm panel using ASI panel identifiers; concordance NIC codes to NIC-2004; match ASICC product codes to dereservation lists; drop closed/missing firms; deflate nominal variables using WPI
3. **Variable construction:** Compute log GVA, log employment, log capital; estimate TFP via Levinsohn-Petrin at 3-digit level; compute fraction of unreserved output using base-year (2000) product shares; create multiproduct and reservation status dummies
4. **Econometric estimation:** Estimate baseline DID (equation 1) with firm and year FE; estimate augmented specifications with triple interactions (multiproduct × unreserved firm × treatment); cluster standard errors at 3-digit industry-year level; use ASI sampling weights
5. **Robustness checks:** Pre-trend falsification tests (lead treatment); placebo regressions with randomised treatment; exclude specific industries; test alternative base years; verify with industry-level regressions

#### 5.4 Potential Challenges in Indian Replication
- ASI panel identifiers have limited availability and quality before 2000; tracking firms across years is imperfect
- Concordance between ASICC product codes (used in ASI) and government dereservation notification codes requires manual matching
- Levinsohn-Petrin TFP estimation requires careful implementation (choice of proxy variables, industry-level estimation)
- Sampling design changes (census vs. sample sector thresholds) affect representativeness over time
- Dereservation is nearly complete post-2014, so extending the analysis requires a different policy variation

### 6. Replication Difficulty Level
**Hard** – Requires access to ASI unit-level panel data with product-level detail, construction of a non-trivial treatment variable from government notifications, and TFP estimation.

### 7. Recommended for Student Replication?
**With caution** – Best suited for advanced graduate students with experience in micro-econometrics and access to ASI unit-level data; the DID methodology is well-documented and the paper provides a clear roadmap.

---

## Paper 13: Regional Concentration of Unorganised Manufacturing Sector in India: A Spatial Analysis

### 1. Citation
* Authors: Ankur Yadav and Hema Prakash
* Year: 2020
* Journal/Working Paper: Jharkhand Journal of Development and Management Studies (XISS, Ranchi), Vol. 18, No. 1 & 2, Jan.–June 2020, pp. 8395–8409
* DOI/Link: Not specified

### 2. Abstract (Concise Summary)
This study analyses the regional disparity of the unorganised manufacturing sector (UMS) and the broader unorganised sector (US) in India using data from the NSSO 73rd round (2015–16). The authors examine spatial distribution across Indian regions and states using the number of enterprises, value of fixed assets, gross value added, and total workers as key indicators. Concentration Ratios (CR) and Location Herfindahl-Hirschman Index (HHI) are computed to assess the degree of spatial concentration at aggregate and disaggregated regional levels. Findings reveal significant regional disparity, with South and West India dominating in terms of GVA and fixed assets, while East India leads in the number of enterprises. The study highlights that the unorganised manufacturing sector is unevenly distributed, with policy implications for balanced regional industrial development.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (six broad regions: North, South, East, West, Central, Northeast) |
| Data Source | NSSO 73rd round on 'Unincorporated Non-Agricultural Enterprises (excluding construction) in India', 2015–16 |
| Time Period | 2015–16 |
| Unit of Analysis | Region and state |
| Sample Size | All states/UTs aggregated into 6 regions |
| Key Variables | Number of enterprises; value of fixed assets; total workers employed; gross value added (GVA); Concentration Ratio (CR); Location Herfindahl-Hirschman Index (HHI) |

### 4. Econometric Methodology
- **Model type:** Descriptive spatial analysis using concentration indices
- **Main measures:**
  - Concentration Ratio (CR): Sum of shares of the top regions in a given variable (enterprises, fixed assets, GVA, workers)
  - Location Herfindahl-Hirschman Index (HHI): HHI = Σ(s_i)², where s_i is the share of region/state i
  - Regional shares computed for enterprises, fixed assets, employment, and GVA
- **Identification strategy:** Purely descriptive; no causal inference
- **Key assumptions:** NSSO 73rd round data is representative at the state/regional level; regional classification into six zones is meaningful for policy analysis

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| NSSO 73rd round (2015–16) | Same data or updated surveys | MOSPI/NSSO unit-level data; also Periodic Labour Force Survey for employment comparisons |
| State-level aggregates | Economic Census (latest: 7th EC, 2019) | Ministry of Statistics, Economic Census data |

#### 5.2 Suggested Variable Mapping
- Direct replication: all variables from NSSO 73rd round
- For updates: use Economic Census 2019 or any newer NSSO enterprise surveys
- Regional classification: six zones (North, South, East, West, Central, Northeast) as per standard planning commission demarcation

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Download NSSO 73rd round unit-level data from MOSPI website (available for purchase); alternatively use published reports for aggregate tabulations
2. **Data cleaning:** Classify states into six regional groups; aggregate enterprise-level data by region and state; apply NSS multipliers for state-level representativeness
3. **Variable construction:** Compute regional shares for each variable (enterprises, fixed assets, workers, GVA); calculate CR (top 3 or 4 regions) and HHI for each variable
4. **Econometric estimation:** Compute and tabulate CR and HHI; compare across regions; create bar charts and maps for spatial distribution
5. **Robustness checks:** Compute for sub-sectors (manufacturing vs. services); compare with earlier NSSO rounds (67th, 62nd); use alternative concentration measures (Gini, Theil index)

#### 5.4 Potential Challenges in Indian Replication
- NSSO unit-level data may require purchase and careful handling of sampling weights
- Published aggregate tables may not provide sufficient detail for sub-regional analysis
- Definitional changes across NSSO rounds (enterprise size thresholds) may affect comparability over time
- The study is entirely descriptive with limited analytical depth

### 6. Replication Difficulty Level
**Easy** – The methodology involves simple concentration ratio and HHI computations from publicly available survey data.

### 7. Recommended for Student Replication?
**Yes** – Very suitable for undergraduate or early graduate students as an introduction to working with NSSO data and computing spatial concentration indices.

---

## Paper 14: Industrial Location and Spatial Inequality: Theory and Evidence from India

### 1. Citation
* Authors: Somik Vinay Lall and Sanjoy Chakravorty
* Year: 2005
* Journal/Working Paper: Review of Development Economics, 9(1), 47–68
* DOI/Link: https://doi.org/10.1111/j.1467-9361.2005.00263.x

### 2. Abstract (Concise Summary)
This paper argues that spatial inequality of industrial location is a primary driver of spatial income inequality in developing nations, using India as a case study. The analysis has two components. First, the authors estimate a translog cost function augmented with economic geography variables (market access, own-industry concentration, interindustry backward linkages, and economic diversity) using plant-level ASI data for 1998–99 across eight manufacturing sectors, finding that local industrial diversity is the only factor with significant and substantial cost-reducing effects. Second, they analyse the determinants of new post-reform industrial investment location at the district level using logistic and OLS regression models, showing that private sector investments strongly favour existing industrial clusters and coastal districts, while central government investments are less spatially biased. The authors conclude that structural reforms and liberalisation have led to increased spatial concentration of industry and, consequently, greater spatial income inequality.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (district-level, ~405 districts) |
| Data Source | Annual Survey of Industries (ASI) 1998–99, unit-level data; ASI Sampling Frame 1998–99 (universe of establishments); Input-Output Transactions Table 1993–94 (Ministry of Statistics); Census data; Indian road network data |
| Time Period | Cross-section: 1998–99 (cost function); 1992–98 (new investment location analysis) |
| Unit of Analysis | Plant/factory (cost function analysis); district (location analysis) |
| Sample Size | ~12,000+ factories across 8 sectors (cost function); 405 districts (location analysis); 292 districts with private investment, 164 with central government investment |
| Key Variables | **Cost function:** total cost, output, input prices (capital, labour, energy, materials), market access index, own-industry employment, backward linkage index, Herfindahl diversity index, urban/metro/rural dummies, public/private dummy, firm age. **Location analysis:** new investment (private and central government), pre-reform investment (asi-log), population, manufacturing labour share, labour and capital productivity, physical infrastructure index, literacy, infant mortality, socialist state dummy, coastal dummy, metropolitan dummy, spatial lag |

### 4. Econometric Methodology
- **Model type:** (1) Translog cost function estimated by SUR (seemingly unrelated regressions) with factor share equations; (2) Logistic regression (binary: investment/no investment) and OLS regression (quantity of investment) for district-level location analysis
- **Main estimating equations:**
  - Translog cost function: ln C_r = α₀ + α_y·ln Y + Σα_j·ln w_j + Σα_l·ln A_l + ½β_yy·(ln Y)² + Σβ_jk·ln w_j·ln w_k + Σγ_lq·ln A_l·ln A_q + Σγ_jl·ln w_j·ln A_l + ...
  - Cost elasticity w.r.t. agglomeration: ∂ ln C / ∂ ln A_l = α_l + Σγ_lq·ln A_q + Σγ_jl·ln w_j + γ_ly·ln Y
  - Location model (logistic): P(I_new > 0) = f(asi-log, ind_credit, capital_prod, logpop, labor_manuf, labor_prod, infra, literacy, infnt_mort, socialist, coastal, metropolitan, spatial_lag)
  - Location model (OLS): ln(I_new) = same regressors (for nonzero investment districts only)
- **Identification strategy:** Cost function exploits cross-sectional variation in economic geography across districts; location analysis uses pre-reform investment as proxy for agglomeration advantages; spatial lag corrects for spatial autocorrelation
- **Key assumptions:** Translog functional form is adequate; agglomeration benefits not fully capitalised in input prices; pre-reform industrial location is predetermined relative to post-reform investment decisions; ASI data captures the universe of formal manufacturing

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI 1998–99 unit-level data | Latest ASI unit-level data (e.g., 2017–18 or later) | MOSPI ASI unit-level data |
| ASI Sampling Frame | ASI Sampling Frame (periodically updated) | CSO/MOSPI |
| Input-Output Transactions Table 1993–94 | Updated I-O tables (2007–08 or 2015–16) | MOSPI Input-Output Transactions Tables |
| Census population data | Census 2011 | Registrar General of India |
| Road network data | Updated road network / PMGSY data | NHAI; Ministry of Road Transport; OpenStreetMap |
| New investment data | New factory registrations / CMIE CapEx data | ASI Sampling Frame (new registrations); CMIE CAPEX database |

#### 5.2 Suggested Variable Mapping
- Market access: Reconstruct gravity-based index using updated road network and Census 2011 urban population
- Own-industry concentration: Compute from latest ASI Sampling Frame employment data at district level
- Backward linkages: Use latest I-O table technical coefficients weighted by district location quotients
- Herfindahl diversity: Compute from district-level employment shares across industries
- New investment: Use new factory registrations from ASI sampling frame or CMIE CapEx data

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain ASI unit-level data for recent year; obtain ASI sampling frame for district-level employment data; acquire I-O tables; obtain Census 2011 district-level data; obtain road network GIS data
2. **Data cleaning:** Match factory data to districts; construct district-level aggregates of economic geography variables; compute market access index using gravity model with road network distances; compute location quotients, backward linkage indices, Herfindahl diversity indices
3. **Variable construction:** Compute total cost, output, input prices from ASI; construct agglomeration variables; identify new investment flows from sampling frame comparisons; create spatial lag variables using district contiguity matrices
4. **Econometric estimation:** Estimate translog cost function with SUR and factor share equations for each sector; compute cost elasticities w.r.t. each economic geography variable; estimate logistic and OLS models for new investment location
5. **Robustness checks:** Test with different functional forms; vary the spatial extent of agglomeration variables; use alternative market access measures; test for spatial dependence using Moran's I; control for state fixed effects

#### 5.4 Potential Challenges in Indian Replication
- Constructing the market access index requires GIS processing of road network data and gravity model computation
- Backward linkage computation requires matching I-O sector classifications to NIC industry codes at the district level
- District boundaries have changed significantly since 1998 (number of districts increased from ~400 to ~730); a temporal concordance is necessary
- ASI sampling frame is not easily accessible for all years
- Spatial lag construction requires district-level contiguity/distance matrices
- SUR estimation of the translog cost function requires specialised software (e.g., Stata's `sureg`, R's `systemfit`)

### 6. Replication Difficulty Level
**Hard** – Requires advanced econometric skills (translog cost function, SUR estimation, spatial econometrics), GIS data processing for market access computation, and extensive data matching across multiple sources.

### 7. Recommended for Student Replication?
**With caution** – Best suited for advanced graduate students or research assistants with GIS and spatial econometrics training; the cost function component alone could serve as a focused replication exercise.

---
---

## Paper 15: Subcontracting and the Size and Composition of the Informal Sector: Evidence from Indian Manufacturing

### 1. Citation
* **Authors:** Ana I. Moreno-Monroy, Janneke Pieters, Abdul A. Erumban
* **Year:** 2012
* **Journal/Working Paper:** IZA Discussion Paper No. 6785, Institute for the Study of Labor (IZA)
* **DOI/Link:** http://hdl.handle.net/10419/62588

### 2. Abstract (Concise Summary)
This paper examines the relationship between formal sector subcontracting and the evolution of the informal manufacturing sector in India during 1994–2006. The authors contrast a "modernization" view (subcontracting promotes upgrading in the informal sector) against a "stagnation" view (subcontracting perpetuates low-wage traditional activities). Using enterprise-level data aggregated to the state-industry level, the study finds that formal sector subcontracting is positively related to the size of the most modern segment of the informal sector, supporting the modernization hypothesis. No evidence is found that increased outsourcing by formal firms drives expansion of very traditional informal activities.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (16 major states + Delhi) |
| Data Source | Annual Survey of Industries (ASI) for formal sector; National Sample Survey (NSS) of Unorganized Manufacturing for informal sector |
| Time Period | 1994–95, 2000–01, 2005–06 |
| Unit of Analysis | State-industry level (2-digit NIC), aggregated from enterprise-level data |
| Sample Size | Unbalanced panel of up to 20 industries × 17 states across 3 time points |
| Key Variables | Informal sector size (employment, hired workers, number of enterprises, real wage bill); formal sector subcontracting (purchase value of goods sold in same condition + cost of contract work); modernity index (log ratio of enterprises outside household to those inside) |

### 4. Econometric Methodology
- **Model type:** Panel fixed effects regression with interaction terms
- **Main estimating equations:**
  - Eq. (1): ln(Y_ist) = α_is + β₁ ln(FS)_ist + β₂ M_ist + β₃ ln(FS)_ist × M_ist + π_st + µ_it + ε_ist
  - Eq. (2): Quartile-based specification allowing discontinuous effects at each modernity quartile
- **Identification strategy:** State-industry fixed effects absorb time-invariant heterogeneity; state-year and industry-year dummies control for time-varying common shocks at state and industry levels
- **Key assumptions:** No strict causal claim due to potential reverse causality (absence of a valid instrument); within-group variation is informative; modernity index captures meaningful heterogeneity in informal sector composition

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI (formal manufacturing) | ASI (latest rounds) | MoSPI Annual Survey of Industries (available up to 2021–22) |
| NSS Unorganized Manufacturing | NSS UMSE / ASUSE | NSS 73rd Round (2015–16) and ASUSE (2021–22 onward, annual) |
| National Accounts (GDP in unregistered manufacturing) | NAS data | CSO/MoSPI National Accounts Statistics |

#### 5.2 Suggested Variable Mapping
- **Informal sector employment/enterprises/wages:** Directly available from NSS unorganized manufacturing surveys
- **Formal sector subcontracting:** ASI Block-H variables (cost of contract/commission work done by others, purchase value of goods sold in same condition)
- **Modernity index:** Location of enterprise (within/outside household) available in NSS enterprise schedule
- **State-industry identifiers:** NIC 2-digit codes matched across ASI and NSS

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain ASI unit-level data from MoSPI and NSS unorganized manufacturing unit-level data (62nd, 67th, 73rd rounds, and ASUSE) from NSSO
2. **Data cleaning:** Harmonize NIC codes across rounds (NIC-1998, NIC-2004, NIC-2008); apply NSS multipliers to generate population estimates; deflate monetary variables using industry-specific WPI
3. **Variable construction:** Aggregate enterprise-level data to state × 2-digit industry level; compute modernity index (ratio of outside-household to inside-household enterprises); calculate formal sector subcontracting from ASI
4. **Econometric estimation:** Estimate panel fixed effects models with state-industry, state-year, and industry-year fixed effects; interact subcontracting with modernity index (continuous and quartile specifications)
5. **Robustness checks:** Use alternative modernity measures (capital per worker, share of hired labor); control for formal sector employment; test sensitivity to sample restrictions (exclude Delhi, small industries)

#### 5.4 Potential Challenges in Indian Replication
- NSS unorganized surveys are quinquennial until 2015–16; ASUSE (annual from 2021–22) uses a different sampling frame, complicating time-series comparability
- NIC concordance across multiple revisions requires careful mapping
- Subcontracting in ASI captures all outsourcing (to both formal and informal), not just formal-to-informal linkages
- Reverse causality remains unaddressed without a suitable instrument

### 6. Replication Difficulty Level
**Moderate** — Data are publicly available and the econometric approach (panel FE) is standard, but constructing the state-industry panel from unit-level data across multiple survey rounds requires significant data processing effort and careful NIC concordance.

### 7. Recommended for Student Replication?
**Yes** — Well-defined methodology, publicly accessible data, and clear variable definitions make this a tractable and instructive replication exercise.

---

## Paper 16: The Indian Manufacturing Sector: Finance, Investment and Performance of Firms

### 1. Citation
* **Authors:** Manmohan Agarwal, Rumi Azim
* **Year:** 2021
* **Journal/Working Paper:** NIPFP Working Paper No. 339, National Institute of Public Finance and Policy
* **DOI/Link:** https://www.nipfp.org.in/publications/working-papers/1936/

### 2. Abstract (Concise Summary)
This paper investigates whether financial stress (high leverage and debt overhang) caused the investment slowdown in Indian manufacturing firms during 2005–2019. Using firm-level data on 804 manufacturing companies classified by market capitalization (large, mid, and small cap), the authors estimate a system of three simultaneous dynamic panel equations for investment growth, debt-equity ratio, and profitability using two-step GMM. The study does not find substantial evidence that financial stress is a major determinant of the investment slowdown. Instead, declining sales growth emerges as the primary factor behind falling fixed investment and profits, supporting the pecking order theory of capital structure, particularly for larger firms.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | CMIE Prowess database (firm balance sheets and income statements); CMIE PACE (credit ratings) |
| Time Period | 2005–2019 |
| Unit of Analysis | Firm-level (listed manufacturing companies) |
| Sample Size | 804 firms (263 large cap, 284 mid cap, 257 small cap) |
| Key Variables | Investment rate (change in gross fixed assets), debt-equity ratio, return on assets, sales growth, firm size (log sales), age, market-to-book value, cash flow/capital, non-debt tax shields, liquidity, tax burden |

### 4. Econometric Methodology
- **Model type:** Simultaneous dynamic panel data model with firm and year fixed effects
- **Main estimating equations (system of 3):**
  - INV_it = α_i + β₁INV_it-1 + β₂ROA_it-1 + β₃DE_it-1 + β₄SIZE_it + β₅AGE_it + β₆GR_it + β₇MBV_it + β₈CF_it-1 + n_t + ε₁_it
  - DE_it = α_i + β₁DE_it-1 + β₂INV_it-1 + β₃ROA_it-1 + β₄SIZE_it + β₅AGE_it + β₆GR_it + β₇NDTS_it + n_t + ε₂_it
  - ROA_it = α_i + β₁ROA_it-1 + β₂DE_it-1 + β₃INV_it-1 + β₄SIZE_it + β₅AGE_it + β₆GR_it + β₇LIQ_it-1 + β₈MBV_it-1 + β₉TAX_it + n_t + ε₃_it
- **Identification strategy:** Two-step feasible efficient GMM using exogenous variables as instruments; Hausman test confirms fixed effects and endogeneity of investment, leverage, and profitability; Hansen's J test for instrument validity
- **Key assumptions:** Investment, leverage, and profitability are jointly endogenous; dynamic persistence in financial variables; valid moment conditions (no second-order serial correlation confirmed by m2 test)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| CMIE Prowess | CMIE Prowess (same source, updated) | CMIE Prowess database (subscription-based) |
| CMIE PACE (credit ratings) | CMIE PACE | CMIE PACE database |

#### 5.2 Suggested Variable Mapping
- All variables are directly replicable from Prowess: gross fixed assets, debt, equity, PAT, total assets, sales, market capitalization, depreciation, current assets/liabilities, tax
- Capital stock: Use perpetual inventory method with GFA data
- Market capitalization cutoffs may need updating for current price levels

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Extract firm-level panel data from CMIE Prowess for manufacturing firms; classify into large/mid/small cap using market capitalization thresholds
2. **Data cleaning:** Retain firms with at most 5 years of missing data in key variables over the sample period; winsorize at 1st and 99th percentiles
3. **Variable construction:** Compute investment rate, ROA, D/E ratio, sales growth, MBV, cash flow/capital, NDTS, liquidity, tax burden as defined in the paper
4. **Econometric estimation:** Estimate three equations separately for each capitalization group using (a) OLS FE without dynamics, (b) two-step GMM without dynamics, (c) two-step GMM with lagged dependent variable; report Hansen's J and m2 tests
5. **Robustness checks:** Vary market capitalization thresholds; extend time period to post-2019; test alternative profitability measures (EBITDA/assets); include sector dummies

#### 5.4 Potential Challenges in Indian Replication
- Prowess is subscription-based and may not be available to all students
- Market capitalization thresholds (Rs 1,000M and Rs 10,000M as of March 2015) need adjustment for inflation if extending the sample period
- Survivorship bias: firms that go bankrupt/delist during the period are excluded
- GMM estimation with many instruments relative to cross-sections may produce unreliable results for small-cap subsamples

### 6. Replication Difficulty Level
**Moderate** — The econometric methodology (system GMM) is well-established but technically demanding; data extraction from Prowess is straightforward but requires institutional access.

### 7. Recommended for Student Replication?
**With caution** — Suitable for advanced students familiar with dynamic panel GMM methods; requires access to CMIE Prowess database.

---

## Paper 17: Partial Privatization and Firm Performance

### 1. Citation
* **Authors:** Nandini Gupta
* **Year:** 2005
* **Journal/Working Paper:** The Journal of Finance, Vol. 60, No. 2
* **DOI/Link:** https://doi.org/10.1111/j.1540-6261.2005.00753.x

### 2. Abstract (Concise Summary)
This paper examines whether partial privatization — the sale of minority government stakes through public equity offerings without transferring management control — improves the performance of state-owned enterprises in India. Using accounting data on the population of non-financial SOEs owned by central and state governments (1990–2002), the study finds that a 10-percentage point decrease in government ownership leads to significant increases in sales (13%), profits (10%), average labor productivity (8%), and R&D investment. The results are robust to dynamic GMM estimation, alternative control groups, and controls for competition policy changes, supporting the hypothesis that stock market listing addresses managerial rather than political inefficiency in SOEs.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | CMIE Prowess database; Department of Public Enterprises (Public Enterprise Survey); World Bank Privatization Database; company annual reports |
| Time Period | 1990–2002 (main analysis 1990–2000) |
| Unit of Analysis | Firm-level (state-owned enterprises) |
| Sample Size | 339 firms (247 central government, 92 state government); up to 2,414 firm-years; main analysis uses 2,230 firm-years (1990–2000) |
| Key Variables | Profitability (log sales, log profit), labor productivity (sales/employment, operating income/labor), investment (log R&D, R&D intensity, capex/sales), employment; PRIV (lagged share of private ownership), government financing share, gross fixed assets |

### 4. Econometric Methodology
- **Model type:** Firm fixed effects regression; Arellano-Bond dynamic GMM as robustness
- **Main estimating equation:**
  - y_it = α_i + α₁ PRIV_it-1 + α₂ X_it-1 + α_t Year_t + ε_it
  - where y_it = performance measure, PRIV_it-1 = lagged private ownership share, X_it-1 = lagged firm controls
- **Identification strategy:** Firm fixed effects control for time-invariant unobserved heterogeneity; lagged privatization variable addresses simultaneity; year dummies control for macroeconomic trends; dynamic GMM instruments privatization with within-panel instruments; dynamic selection bias controlled using Frydman et al. (1999) method restricting control group
- **Key assumptions:** Strict exogeneity in FE model (relaxed in GMM); privatization is not driven by prior-year unusually bad performance (tested and rejected); no agency cost increase from ownership dilution in SOEs (unlike private firms)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| CMIE Prowess (SOE financials) | CMIE Prowess (updated) | CMIE Prowess database |
| Public Enterprise Survey | Public Enterprise Survey (annual) | Department of Public Enterprises, Government of India |
| Privatization transaction data | DPE + DIPAM records | Department of Investment and Public Asset Management (DIPAM) |
| CEO/board turnover data | Company annual reports / MCA filings | Ministry of Corporate Affairs (MCA21 database) |

#### 5.2 Suggested Variable Mapping
- **PRIV:** Government equity share from DPE/DIPAM records; compute private share = 1 − government share
- **Performance variables:** Sales, profit, employment, R&D, capex from Prowess
- **Government financing:** Loans and subsidies from government from balance sheet data
- **Competition controls:** Include post-1991 trade liberalization and delicensing dummies

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Identify the population of central and state PSEs from the Public Enterprise Survey; extract financial data from CMIE Prowess; collect privatization transaction details from DIPAM
2. **Data cleaning:** Match PSE identifiers across Prowess and DPE datasets; construct unbalanced panel; handle firms that underwent strategic disinvestment separately
3. **Variable construction:** Compute log sales, log profit, labor productivity ratios, R&D intensity, capex/sales; construct PRIV as lagged private ownership share
4. **Econometric estimation:** Estimate firm FE models with year dummies; replicate dynamic GMM (Arellano-Bond) for growth rate specifications; test restricted control groups (firms likely to be privatized)
5. **Robustness checks:** Exclude oil & gas firms; separate central vs. state PSEs; extend period to cover post-2000 strategic sales; test pre-privatization performance trends

#### 5.4 Potential Challenges in Indian Replication
- Post-2000, the privatization program shifted to strategic sales (majority stakes), making the partial privatization analysis less relevant for recent data
- Employment data for state-government-owned firms is limited
- CEO/board turnover data requires manual collection from annual reports
- The population of PSEs has changed significantly (new PSEs created, mergers, closures)

### 6. Replication Difficulty Level
**Hard** — Requires assembling data from multiple sources (Prowess, DPE, DIPAM, annual reports); the population of firms is specialized; dynamic GMM with within-panel instruments for ownership is technically demanding.

### 7. Recommended for Student Replication?
**With caution** — Excellent for learning about privatization impact evaluation, but the data collection effort (especially for ownership changes and management turnover) is substantial; best suited for PhD-level research.

---

## Paper 18: The Impact of FDI Inflows on R&D Investment by Medium- and High-Tech Firms in India in the Post-Reform Period

### 1. Citation
* **Authors:** Vinish Kathuria
* **Year:** 2008
* **Journal/Working Paper:** Transnational Corporations, Vol. 17, No. 2 (August 2008), UNCTAD
* **DOI/Link:** Not available (UNCTAD publication)

### 2. Abstract (Concise Summary)
This study investigates the effect of FDI inflows on the R&D activities of domestic firms in medium- and high-tech manufacturing industries in India after the 1991 liberalization. It makes two methodological contributions: (i) accounting for firms with in-house R&D units recognized by the Department of Science and Technology (DST) but reporting zero R&D expenditure, and (ii) using actual FDI inflows rather than approvals. Using probit and tobit models on firm-level data for 190 firms across seven industries, the paper finds that in the initial post-reform period (1994–1996), increased FDI inflows had a significant negative impact on domestic firms' propensity to invest in R&D. In the later period (1999–2001), the negative effect becomes statistically insignificant.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Capitaline database (Capital Market); DST records for in-house R&D unit recognition; SIA (Secretariat for Industrial Assistance) for actual FDI inflows |
| Time Period | Two cross-sections: 1996 (averaging 1994–96) and 2001 (averaging 1999–2001) |
| Unit of Analysis | Firm-level (listed private manufacturing firms in medium- and high-tech industries) |
| Sample Size | 190 firms across 7 industries (auto ancillaries, chemicals, electrical equipment, electronic components, engineering, petrochemicals, pharmaceuticals) |
| Key Variables | R&D dummy (DST R&D unit or reported R&D expenditure); R&D intensity (R&D/sales); cumulative FDI inflows at industry level; firm size (log gross assets); export intensity; Herfindahl index; foreign ownership share; vertical integration; royalty payments |

### 4. Econometric Methodology
- **Model type:** Probit (for binary R&D decision) and Tobit (for censored R&D intensity)
- **Main estimating equation:**
  - RD (or RDI) = β₁ + β₂×FDI_t-1 + β₃×ln(Size) + β₄×Export Intensity + β₅×H-index + β₆×Foreign Share + β₇×Vertical Integration + β₈×Royalty + u
  - In probit: RD = 1 if firm has DST R&D unit or reports R&D expenditure, 0 otherwise
  - In tobit: RDI = R&D expenditure / total sales
- **Identification strategy:** Cross-sectional variation across firms within medium- and high-tech industries; FDI measured as cumulative actual inflows at industry level (lagged); comparative analysis across two time periods
- **Key assumptions:** Cross-sectional independence; FDI inflows at industry level are exogenous to individual firm R&D decisions; tobit assumes normality and homoscedasticity of the latent variable; firms incorporated before 1991 (cohort consistency)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| Capitaline database | CMIE Prowess | CMIE Prowess (more comprehensive, subscription-based) |
| DST R&D unit recognition | DSIR recognized R&D centers list | Department of Scientific and Industrial Research (DSIR) website |
| SIA FDI inflows | DPIIT FDI data | Department for Promotion of Industry and Internal Trade (DPIIT) — FDI statistics by industry |

#### 5.2 Suggested Variable Mapping
- **R&D expenditure / R&D intensity:** Available in Prowess (R&D expenditure line item)
- **In-house R&D unit:** DSIR publishes list of recognized in-house R&D centers
- **FDI inflows by industry:** DPIIT publishes annual FDI equity inflows by sector
- **Firm size, exports, foreign equity, value added, royalty payments:** All available in Prowess
- **Herfindahl index:** Computed from Prowess sales data at NIC 3-digit level

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Extract firm-level data from CMIE Prowess for manufacturing firms in medium- and high-tech industries; obtain FDI inflow data by industry from DPIIT; obtain DSIR R&D center list
2. **Data cleaning:** Exclude post-liberalization entrants (if replicating original design) or include all firms for an extended study; exclude regulated/SSI industries; retain firms with data in both cross-sections
3. **Variable construction:** Compute R&D intensity; construct binary R&D variable using both expenditure reporting and DSIR recognition; compute industry-level cumulative FDI; calculate H-index from firm-level sales
4. **Econometric estimation:** Run probit regressions for both R&D measures; run tobit regression for R&D intensity; compare coefficients across periods
5. **Robustness checks:** Use panel probit/tobit if extending to multiple years; instrument FDI with approval data or lagged FDI; test with alternative industry classifications (NIC 2-digit vs. 3-digit)

#### 5.4 Potential Challenges in Indian Replication
- Capitaline database used in the original study is different from Prowess; variable definitions may differ slightly
- Matching DSIR R&D center list to firm-level data requires manual effort
- Industry-level FDI data from DPIIT may not map cleanly to NIC codes used in firm-level databases
- Cross-sectional design limits causal inference; panel methods would improve identification but require more data

### 6. Replication Difficulty Level
**Moderate** — Probit and tobit models are standard; the main challenge is matching FDI inflow data at the industry level with firm-level R&D data and obtaining the DSIR R&D unit information.

### 7. Recommended for Student Replication?
**Yes** — The econometric methods are straightforward (probit/tobit), the sample is small and manageable, and the research question remains highly relevant for studying FDI-R&D linkages in India.

---

## Paper 19: Assessing Regional Manufacturing Productivity in India: A Comparative Analysis of Organised and Unorganised Manufacturing

### 1. Citation
* **Authors:** Mahua Paul, Smruti Ranjan Sahoo
* **Year:** 2025
* **Journal/Working Paper:** ISID Working Paper No. 299, Institute for Studies in Industrial Development
* **DOI/Link:** https://isid.org.in (ISID Working Paper series)

### 2. Abstract (Concise Summary)
This study assesses regional Total Factor Productivity (TFP) across India's organised and unorganised manufacturing sectors for 18 major states over 2000–01 to 2022–23. Using the Ackerberg, Caves, and Frazer (2015) semi-parametric method to estimate a gross value-added production function at the NIC 4-digit level for 22 industry groups, the paper reveals a dual-track evolution: the organised sector shows maturation and consolidation in productivity (especially in chemicals, textiles, and leather since 2010), while the unorganised sector exhibits mixed performance with sharp divergence across states after 2010. The findings underscore significant regional and sectoral disparities, calling for targeted policy interventions to promote technological adoption in the unorganised sector.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (18 major states) |
| Data Source | Annual Survey of Industries (ASI) for organised sector; NSS Unorganised Manufacturing Surveys (UMSE: 2000–01, 2005–06, 2010–11, 2015–16) and Annual Survey of Unincorporated Sector Enterprises (ASUSE: 2021–22, 2022–23) for unorganised sector |
| Time Period | 2000–01 to 2022–23 |
| Unit of Analysis | Plant/establishment level, aggregated to NIC 4-digit industry × state level |
| Sample Size | 22 industry groups at NIC 4-digit level across 18 states (covering ~93% of total manufacturing GVA and ~91% of factories) |
| Key Variables | Gross Value Added (GVA), labour (workers/person-days), capital (constructed via perpetual inventory method), intermediate inputs (materials); TFP estimated as residual from ACF production function |

### 4. Econometric Methodology
- **Model type:** Semi-parametric production function estimation using Ackerberg, Caves, and Frazer (2015) method
- **Main estimating equation:**
  - Production function: lnGVA_it = α + β_l × lnL_it + β_c × lnK_it + u_it
  - where u_it = ω_it (productivity) + e_it (random error)
  - Productivity proxy: ω_it = g⁻¹(int_it, k_it) using intermediate inputs
  - TFP_it = lnGVA_it − β̂_l × lnL_it − β̂_c × lnK_it
  - Weighted TFP: WTFP_it = TFP_it × share_it; aggregated to state level
- **Identification strategy:** ACF method addresses endogeneity of input choices by using intermediate inputs as a proxy for unobserved productivity shocks; both labour and capital coefficients identified in the second stage, avoiding the functional dependency problem of Olley-Pakes and Levinsohn-Petrin methods
- **Key assumptions:** Scalar unobservability (productivity is a scalar function of intermediate inputs and capital); first-order Markov process for productivity evolution; monotonicity of intermediate input demand in productivity; timing assumptions (capital decided one period ahead, labour freely adjustable)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI unit-level data | ASI (same source) | MoSPI Annual Survey of Industries |
| NSS UMSE / ASUSE | NSS UMSE / ASUSE (same source) | National Sample Survey Office / National Statistical Office |

#### 5.2 Suggested Variable Mapping
- **GVA:** Output minus intermediate consumption (directly available in ASI; constructed from NSS enterprise data)
- **Labour:** Total persons engaged or man-days worked (ASI); workers and working days (NSS)
- **Capital:** Constructed via perpetual inventory method (PIM) using fixed assets, depreciation, and investment data
- **Intermediate inputs:** Total material inputs consumed (ASI Block-H; NSS expenditure blocks)
- **Price deflators:** WPI at commodity level for single/double deflation of GVA

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain ASI unit-level data from MoSPI for 2000–01 to 2022–23; obtain NSS UMSE (rounds 56, 62, 67, 73) and ASUSE data from NSSO
2. **Data cleaning:** Concord NIC revisions (NIC-1998, NIC-2004, NIC-2008) to a consistent NIC-2008 classification; handle outliers in unit-level data; apply multipliers for NSS sample data
3. **Variable construction:** Construct real GVA using appropriate deflation method (single or double); construct capital stock using PIM; compute labour input as total person-days
4. **Econometric estimation:** Estimate ACF production function at NIC 4-digit level separately for organised and unorganised sectors; compute plant-level TFP; aggregate to state level using value-added weights
5. **Robustness checks:** Compare ACF with Levinsohn-Petrin and Olley-Pakes estimates; use gross output production function as alternative; test sensitivity to deflation method (SD vs. DD); examine within-industry dispersion of TFP

#### 5.4 Potential Challenges in Indian Replication
- Capital stock construction via PIM requires assumptions about initial capital stock and depreciation rates that can significantly affect TFP estimates
- NSS unorganised sector surveys are quinquennial until 2015–16, creating gaps; ASUSE (annual from 2021–22) has a different survey design
- NIC concordance across four revisions over 23 years is non-trivial
- ASI microdata access may require formal application to MoSPI
- Appropriate deflators at NIC 4-digit level may not be available; researchers often use 2-digit WPI

### 6. Replication Difficulty Level
**Hard** — While the ACF method is well-documented, implementing it at the NIC 4-digit level across both organised and unorganised sectors for 18 states over 23 years requires extensive data processing, careful variable construction (especially capital via PIM), and NIC concordance across multiple revisions.

### 7. Recommended for Student Replication?
**With caution** — Suitable for advanced students or PhD researchers with strong data handling skills; the ACF methodology is well-suited for learning TFP estimation, but the scope of the data exercise is ambitious for a course project. A narrower replication (fewer states or industries, shorter period) is recommended.

---

## Paper 20: Concentration and Other Determinants of Innovative Efforts in Indian Manufacturing Sector: A Dynamic Panel Data Analysis

### 1. Citation
* **Authors:** Rakesh Basant, Pulak Mishra
* **Year:** 2013
* **Journal/Working Paper:** IIM Ahmedabad Working Paper No. 2013-02-01
* **DOI/Link:** Available at IIM Ahmedabad Research and Publications repository

### 2. Abstract (Concise Summary)
This paper examines the role of expected market concentration, alongside other structural, conduct, performance, and policy variables, in determining inter-industry variations in R&D intensity in Indian manufacturing. Drawing on the Kamien-Schwartz (1982) framework that firms' innovative efforts depend on anticipated market power, the authors use the Arellano-Bond dynamic panel data estimation technique on a dataset of 34 manufacturing industries over 2001–02 to 2008–09. The study finds that past R&D intensity, MNC participation, capital intensity, and export orientation positively influence R&D efforts, while mergers and acquisitions and import competition reduce them. Notably, actual market concentration (measured by multiple indices) does not significantly affect R&D intensity.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | CMIE Prowess (firm-level, aggregated to industry level); CMIE Business Beacon (M&A data) |
| Time Period | 2001–02 to 2008–09 |
| Unit of Analysis | Industry-level (34 manufacturing industries) |
| Sample Size | 34 industries × 8 years = panel of up to 272 observations |
| Key Variables | R&D intensity (R&D expenditure/sales); market concentration (Entropy, HHI, Horwath, GRS indices); market size; MNC participation; capital intensity; advertising intensity; technology purchase intensity; M&A count; export intensity; import intensity; profitability; industry risk (CV of profitability) |

### 4. Econometric Methodology
- **Model type:** Arellano-Bond dynamic panel data estimation (GMM)
- **Main estimating equation:**
  - R&D_it = θ₁ + θ₂ R&D_it-1 + θ₃ CON_it + η X_it + ω_it
  - Derived from adaptive expectations model: R&D depends on expected (future) concentration, transformed via Koyck lag and Cagan-Friedman error learning assumptions
  - X includes: MSZ, MNC, KI, ADVT, TPUR, M&A, EXP, IMP, PROF, IR
- **Identification strategy:** Arellano-Bond GMM addresses endogeneity of lagged dependent variable and explanatory variables by using lagged levels as instruments for first-differenced equations; Sargan test for over-identifying restrictions; Arellano-Bond tests for AR(1) and AR(2) in residuals
- **Key assumptions:** Adaptive expectations (expected concentration is linearly related to current concentration via error learning); three-year moving averages smooth annual fluctuations; valid instruments (confirmed by Sargan test); no second-order autocorrelation
- Four alternative concentration measures used to substantiate findings

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| CMIE Prowess (firm-level, aggregated to industry) | CMIE Prowess (same, updated) | CMIE Prowess database |
| CMIE Business Beacon (M&A data) | CMIE Business Beacon | CMIE Business Beacon database |

#### 5.2 Suggested Variable Mapping
- **R&D intensity:** R&D expenditure / net sales from Prowess
- **Concentration indices:** Compute HHI, Entropy, Horwath, GRS from firm-level sales data aggregated to industry
- **MNC participation:** Share of foreign-owned firms' sales in industry sales
- **Capital intensity:** Gross fixed assets per unit of output at industry level
- **M&A count:** Number of M&A transactions from Business Beacon
- **Export/Import intensity:** Industry-level exports/imports as share of sales
- **Profitability, advertising, technology purchase intensity:** From Prowess, aggregated to industry level

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Extract firm-level data from CMIE Prowess for all manufacturing firms; obtain M&A data from Business Beacon; define 34 industry groups (likely NIC 2-digit or 3-digit)
2. **Data cleaning:** Compute three-year moving averages for all variables; aggregate firm-level data to industry level; handle missing values and outliers
3. **Variable construction:** Compute four concentration indices at industry level from firm sales; calculate R&D intensity, capital intensity, MNC share, advertising intensity, technology purchase intensity, export and import intensities, profitability, and industry risk (CV of profitability)
4. **Econometric estimation:** Estimate Arellano-Bond dynamic panel GMM with one-step (for coefficient inference with robust standard errors) and two-step (for Sargan test and model significance); use each of the four concentration measures in separate specifications
5. **Robustness checks:** Extend the sample period beyond 2008–09; use firm-level panel instead of industry-level; test with alternative industry definitions; include patent-related variables if data available

#### 5.4 Potential Challenges in Indian Replication
- Industry-level analysis with only 34 cross-sections limits the power of GMM estimation (instrument count vs. cross-sections)
- Three-year moving averages reduce effective time dimension further
- Industry classification must be consistent across the panel period (NIC changes)
- CMIE Prowess primarily covers listed and large unlisted firms, potentially biasing concentration measures
- M&A data completeness depends on Business Beacon coverage

### 6. Replication Difficulty Level
**Moderate** — The Arellano-Bond estimator is available in standard econometric software (Stata, R); the main challenge is constructing a clean industry-level panel with consistent industry definitions and computing multiple concentration indices.

### 7. Recommended for Student Replication?
**Yes** — Good exercise in dynamic panel methods and industrial organization; the dataset is relatively small and manageable; the research question on the Schumpeterian hypothesis is pedagogically valuable.

---

## Paper 21: Determinants and Impact of Subcontracting: Evidence from India's Informal Manufacturing Sector

### 1. Citation
* **Authors:** Amit Basole, Deepankar Basu, Rajesh Bhattacharya
* **Year:** 2014
* **Journal/Working Paper:** University of Massachusetts Boston, Department of Economics Working Paper 2014-08
* **DOI/Link:** UMass Boston working paper series

### 2. Abstract (Concise Summary)
This paper investigates the determinants and productivity effects of subcontracting on firms in India's informal manufacturing sector. Applying a modified Heckman selection model to firm-level data from the NSS 62nd Round (2005–06), the authors test two competing perspectives: the "benign" view (subcontracting benefits relatively modern informal firms) and the "exploitation" view (formal firms extract surplus from stagnant, asset-poor informal firms using cheap family labor). The study finds that home-based, asset-poor, and female-owned firms are more likely to be subcontracted — consistent with the exploitation view in terms of selection. However, selectivity-corrected Oaxaca-Blinder decomposition and treatment effect analysis reveal that subcontracting provides a small productivity premium, particularly benefiting smaller firms, firms in industrially backward states, and rural firms, while larger firms and firms in advanced states face a subcontracting penalty.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | NSS 62nd Round — Survey of Unorganized Manufacturing Enterprises (2005–06) |
| Time Period | 2005–06 (cross-section) |
| Unit of Analysis | Firm/enterprise-level (informal manufacturing firms) |
| Sample Size | 63,733 enterprises (from original 82,897 after excluding firms with >20 workers and those registered under Factories Act); representing ~15.3 million enterprises using survey weights |
| Key Variables | Gross value added per worker-hour (productivity); subcontracting status (binary); firm location (home-based vs. outside); ownership (male/female); number of workers; assets; state (industrially advanced vs. backward); rural/urban; industry (2-digit NIC) |

### 4. Econometric Methodology
- **Model type:** Modified Heckman selection model (full information maximum likelihood); selectivity-corrected Oaxaca-Blinder decomposition; Average Treatment Effect on the Treated (ATET)
- **Main estimating structure:**
  - **Selection equation (probit):** P(SC=1 | Z) = Φ(Zγ), where Z includes firm characteristics determining subcontracting status
  - **Outcome equation:** ln(GVA per worker-hour) = Xβ + ρσ λ(Zγ) + ε, where λ is the inverse Mills ratio
  - **Oaxaca-Blinder decomposition:** GVA gap = [endowment effect] + [coefficient effect] + [selection effect]
  - **ATET:** E[Y₁ − Y₀ | SC=1], estimated from selection-corrected model
- **Identification strategy:** Exclusion restrictions in the Heckman model (variables in selection equation excluded from outcome equation); FIML estimation avoids two-step inefficiency; decomposition separates GVA gap into endowment differences and returns differences
- **Key assumptions:** Joint normality of errors in selection and outcome equations; valid exclusion restrictions (instruments affect subcontracting decision but not productivity directly); conditional independence for ATET interpretation

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| NSS 62nd Round UMSE (2005–06) | NSS 67th, 73rd Round UMSE; ASUSE | NSS 73rd Round (2015–16) for quinquennial survey; ASUSE 2022–23 for latest annual data |

#### 5.2 Suggested Variable Mapping
- **Subcontracting status:** NSS unorganized manufacturing schedule asks "Did the enterprise work on contract basis during the reference period?" — available in all rounds
- **GVA per worker-hour:** Computed from total receipts minus total expenditure on inputs, divided by total worker-hours (person-days × hours per day)
- **Location:** Home-based vs. establishment (outside household) — standard NSS classification
- **Ownership:** Male/female owner — available in enterprise schedule
- **Assets:** Fixed assets owned/hired — available in NSS enterprise schedule
- **Enterprise type:** OAMEs vs. NDMEs vs. DMEs — standard NSS classification
- **State classification:** Industrially advanced vs. backward — use standard planning commission or NITI Aayog classifications

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain NSS unit-level data for the chosen survey round (73rd Round 2015–16 or ASUSE 2022–23) from NSSO/MoSPI
2. **Data cleaning:** Exclude firms registered under the Factories Act and those with >20 workers; apply survey weights; handle outliers in GVA and worker-hours
3. **Variable construction:** Compute GVA per worker-hour; construct subcontracting binary variable; create dummy variables for location, ownership, enterprise type, state classification, rural/urban
4. **Econometric estimation:** Estimate Heckman selection model via FIML; compute marginal effects from selection equation; perform selectivity-corrected Oaxaca-Blinder decomposition; calculate ATET for full sample and sub-samples (OAMEs vs. non-OAMEs; advanced vs. backward states; rural vs. urban)
5. **Robustness checks:** Use alternative productivity measures (GVA per worker, output per worker); test different exclusion restrictions; compare results across survey rounds; estimate without selection correction (OLS with subcontracting dummy) to demonstrate selection bias

#### 5.4 Potential Challenges in Indian Replication
- NSS data cannot distinguish between formal-to-informal and informal-to-informal subcontracting
- Exclusion restrictions in the Heckman model require careful justification; finding variables that affect subcontracting but not productivity is non-trivial
- ASUSE survey design differs from UMSE, potentially affecting comparability across rounds
- Worker-hours may be measured with error in informal sector surveys (recall bias, seasonal variation)
- Cross-sectional design limits causal interpretation; unobserved firm heterogeneity cannot be controlled

### 6. Replication Difficulty Level
**Moderate** — The Heckman selection model and Oaxaca-Blinder decomposition are well-established techniques available in Stata/R; the NSS data is publicly accessible; the main challenge is careful variable construction and justification of exclusion restrictions.

### 7. Recommended for Student Replication?
**Yes** — Excellent for learning sample selection models and decomposition techniques; the NSS data is large and publicly available; the research question on informal sector subcontracting is policy-relevant and well-framed for a student project.

---
---

## Paper 22: Foreign Investment in Indian Industrial Firms and Its Impact on Firm Performance

### 1. Citation
* **Authors:** Bishwanath Goldar, Akhilesh Kumar Sharma
* **Year:** 2015
* **Journal/Working Paper:** The Journal of Industrial Statistics, Vol. 4, No. 1, pp. 1–18
* **DOI/Link:** Not available

### 2. Abstract (Concise Summary)
This paper investigates whether foreign direct investment (FDI) in Indian manufacturing firms improves their performance, measured through growth (sales), profitability, and export intensity. Using a difference-in-difference (DID) estimator combined with propensity score matching (PSM) on an unbalanced panel of 775 manufacturing companies from 2000–01 to 2011–12, the authors compare firms that transitioned from domestic to foreign ownership with matched control firms. The results show no significant effect of FDI on sales growth or export performance. However, there is weak evidence that FDI may raise profitability after two to three years, possibly reflecting a delayed productivity-enhancing effect.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Ace Equity database |
| Time Period | 2000–01 to 2011–12 |
| Unit of Analysis | Manufacturing firm (company) |
| Sample Size | 775 manufacturing firms; ~3,707 observations for probit model |
| Key Variables | Foreign equity holding %, sales growth (log real sales), profit rate, export intensity, debt-equity ratio, firm size (log gross fixed assets), firm age, investment rate, capital goods imports, royalty & technical fee payments, business group affiliation |

### 4. Econometric Methodology
- **Model type:** Difference-in-Difference (DID) with Propensity Score Matching (PSM)
- **Main estimating equation:** ATT = E[ΔY | D=1] − E[ΔY | D=0, matched], where D=1 denotes foreign acquisition (foreign equity crossing 10% threshold). A Probit model is estimated first for propensity scores:
  - P(Treatment=1) = f(Royalty/sales, Cash flow/sales, Debt-equity ratio, Capital goods imports/GFA, Size, Age dummies, Business group dummy, Foreign equity % (lagged), Export intensity, Import intensity, Investment rate, Industry & Year dummies)
- **Identification strategy:** Treatment defined as foreign equity share crossing 10% threshold; PSM matches treated firms to similar untreated firms within the same year and broad industry group; DID compares pre-post performance changes between treated and matched controls
- **Key assumptions:** Conditional independence (selection on observables); common support; parallel trends in outcomes absent treatment; bootstrapped standard errors for ATT

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| Ace Equity database | CMIE Prowess IQ / Ace Equity | Same database or Prowess IQ for updated firm-level financials and equity holding patterns |
| FDI macro data (DIPP) | RBI / DIPP FDI statistics | Department for Promotion of Industry and Internal Trade (DPIIT) |

#### 5.2 Suggested Variable Mapping
- Foreign equity holding % → Available in Prowess IQ under shareholding pattern
- Sales, profits, exports, debt-equity → Standard financial variables in Prowess IQ
- Business group affiliation → Prowess IQ ownership classification
- Industry classification → NIC 2-digit codes available in Prowess

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Extract firm-level panel from Prowess IQ (2012–2023) with detailed shareholding patterns, filtering for manufacturing companies with available foreign promoter equity data.
2. **Data cleaning:** Identify firms crossing the 10% foreign equity threshold; winsorize key variables at 2.5% level; construct year-wise treatment indicators.
3. **Variable construction:** Compute performance indicators (log real sales growth, profit rate, export intensity); construct lagged explanatory variables for probit model.
4. **Econometric estimation:** Estimate Probit model for propensity scores; perform nearest-neighbor matching within year and broad industry group; compute DID-ATT for 0 to 3 years post-treatment with bootstrapped standard errors.
5. **Robustness checks:** Vary the foreign equity threshold (e.g., 20%, 25%); use alternative matching algorithms (kernel, caliper); test for balance across matched samples; check sensitivity to sample period.

#### 5.4 Potential Challenges in Indian Replication
- Detailed shareholding data (foreign promoter equity %) may be missing for many firms in Prowess
- Sample selection bias: firms with available equity data may disproportionately be larger listed companies
- Defining the exact year of acquisition requires clean annual shareholding data
- Small number of treatment events may limit statistical power

### 6. Replication Difficulty Level
**Moderate** — The DID-PSM methodology is well-established and replicable. The main challenge lies in constructing the clean treatment variable from shareholding data and ensuring adequate sample sizes for matching.

### 7. Recommended for Student Replication?
**Yes** — The paper uses standard causal inference techniques (DID + PSM) that are pedagogically valuable and the data is accessible through Prowess IQ.

---

## Paper 23: Not All Informal Firms Are Alike: Understanding Gender Productivity Gaps across Enterprise Types in India's Informal Manufacturing Sector – Evidence from ASUSE Data

### 1. Citation
* **Authors:** Bishwanath Goldar, Suresh Chand Aggarwal, Abdul A. Erumban
* **Year:** 2025
* **Journal/Working Paper:** Working Paper (November 2025); affiliations: Institute of Economic Growth, Delhi; Institute for Human Development, New Delhi; University of Groningen
* **DOI/Link:** Not available (preprint)

### 2. Abstract (Concise Summary)
This paper examines gender-based productivity gaps in India's informal manufacturing sector, distinguishing between own-account enterprises (OAEs) and manufacturing establishments (MEs) that employ hired workers. Using unit-level data from the Annual Survey of Unincorporated Sector Enterprises (ASUSE) 2023–24, the authors find that the gender productivity gap (measured as GVA per worker) is primarily concentrated among OAEs, particularly single-worker enterprises. Among MEs with more than five workers, no statistically significant productivity difference exists between male- and female-owned firms. The gap narrows further when female-owned enterprises possess higher levels of capital stock. The study highlights that the location of operations (household premises vs. outside) and financial constraints are key drivers of the observed gap.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Annual Survey of Unincorporated Sector Enterprises (ASUSE), NSSO, Ministry of Statistics and Programme Implementation |
| Time Period | 2023–24 (with comparisons to 2022–23 and 2015–16) |
| Unit of Analysis | Unincorporated manufacturing enterprise |
| Sample Size | Full ASUSE sample for manufacturing (exact N not reported; nationally representative micro-data) |
| Key Variables | GVA per worker (labour productivity), gender of enterprise head, enterprise type (OAE vs. ME, further classified into non-directory ME and directory ME), number of workers, capital stock (entrepreneur-owned assets), location of enterprise (household premises vs. outside), industry classification |

### 4. Econometric Methodology
- **Model type:** Primarily descriptive analysis with kernel density estimation, Kolmogorov-Smirnov tests for equality of distributions, t-tests for equality of means, and basic econometric (regression) analysis for heterogeneity within OAEs
- **Main estimating equation:** Descriptive — kernel density comparisons of ln(GVA per worker) across gender, with sub-sample stratification by enterprise type (OAE with 1 worker, OAE with 2+ workers, non-directory MEs, directory MEs)
- **Identification strategy:** Stratified comparison across enterprise types, controlling for number of workers, capital stock thresholds, and location of enterprise; focus on "apples-to-apples" comparisons within narrow enterprise categories
- **Key assumptions:** Sample-weighted estimates reflect population parameters; productivity differences within narrowly defined enterprise types approximate gender-specific effects; cross-sectional identification

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASUSE 2023–24 | ASUSE micro-data (same source) | NSSO/MoSPI unit-level data; earlier rounds available (NSS 73rd round 2015–16, ASUSE 2022–23) |
| Earlier comparisons (2015–16) | NSS 73rd Round (Unincorporated Non-Agricultural Enterprises) | NSSO unit-level data |

#### 5.2 Suggested Variable Mapping
- GVA per worker → Directly available in ASUSE (receipts minus expenses divided by total workers)
- Gender of head → Available as proprietor gender variable
- Enterprise type → OAE vs. Establishment classification in NSSO surveys
- Capital stock → Market value of owned fixed assets
- Location → Whether enterprise operates from household premises or outside

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain unit-level ASUSE 2023–24 data from MoSPI (or use earlier available rounds like NSS 73rd round or ASUSE 2022–23).
2. **Data cleaning:** Filter manufacturing enterprises; classify into OAEs and MEs; further sub-classify MEs into non-directory (<6 workers) and directory (6+ workers); apply sample weights.
3. **Variable construction:** Compute ln(GVA per worker); code enterprise head gender; construct capital stock thresholds (e.g., Rs. 500K, Rs. 1 million); identify location (household premises vs. outside).
4. **Econometric estimation:** Generate kernel density plots of log productivity by gender for each enterprise type; conduct KS tests and t-tests; run basic regressions of ln(productivity) on gender dummy interacted with enterprise type.
5. **Robustness checks:** Vary capital stock thresholds; restrict analysis to specific industries where OAEs dominate; compare across survey rounds for temporal trends.

#### 5.4 Potential Challenges in Indian Replication
- Access to ASUSE 2023–24 unit-level data may require institutional affiliation and formal data request to MoSPI
- Earlier rounds may use different variable definitions or sampling frames
- The paper uses primarily descriptive methods; extending to causal analysis would require additional identification strategies

### 6. Replication Difficulty Level
**Easy** — The analysis is primarily descriptive (kernel densities, t-tests, KS tests) with simple regression. The main requirement is access to the ASUSE micro-data.

### 7. Recommended for Student Replication?
**Yes** — Excellent for students learning descriptive empirical analysis with survey data; accessible methodology and highly policy-relevant research question on gender gaps.

---

## Paper 24: Industry and the Urge to Cluster: A Study of the Informal Sector in India

### 1. Citation
* **Authors:** Megha Mukim
* **Year:** 2011
* **Journal/Working Paper:** SERC Discussion Paper 72, Spatial Economics Research Centre, London School of Economics
* **DOI/Link:** Not available (SERC Discussion Paper series)

### 2. Abstract (Concise Summary)
This paper investigates the determinants of firm location choice at the district level in India to assess the relative importance of agglomeration economies versus business environment factors for the informal (unorganised) sector. Using data from the National Sample Survey covering over 4.4 million firms in unorganised manufacturing and services, the empirical analysis employs count models (Poisson and negative binomial regressions). The count of new informal firm births per district is modelled as a function of localisation economies, inter-industry buyer-supplier linkages, urbanisation economies (diversity), market access, infrastructure, education, and wages. To address endogeneity, the author instruments with historical land revenue institutions. Results indicate that buyer-supplier linkages and industrial diversity significantly attract informal firms, along with infrastructure quality, suggesting that public policy may have limited ability to encourage relocation of informal firms against the forces of agglomeration.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (604 districts) |
| Data Source | NSSO 57th Round (2001–02, Services) and 62nd Round (2005–06, Manufacturing); NSSO Employment-Unemployment Surveys (55th Round 1999–2000, 61st Round 2004–05); Census 2001; National Input-Output Table |
| Time Period | Two cross-sections: Services ~2001–02, Manufacturing ~2005–06 |
| Unit of Analysis | District-industry (NIC 2-digit) |
| Sample Size | ~2.4 million new services firms; ~2.0 million new manufacturing firms across 578–586 districts |
| Key Variables | Dependent: Count of new informal firm births per district-industry. Independent: Localisation economies (own-industry employment share), inter-industry linkages (I-O weighted employment), urbanisation/diversity (Herfindahl index), market access (gravity-based population accessibility), education (share with high school education), infrastructure (electricity access, telephone connections), wages (non-agricultural hourly wages), wealth (high-MPCE household share) |

### 4. Econometric Methodology
- **Model type:** Count models — Poisson regression, Negative Binomial, Zero-Inflated Poisson (ZIP), and Hurdle models
- **Main estimating equation:**
  E(n_{ijk}) = λ_{ijk} = exp(α·d_{ijk} + β·Z_{ijk})
  where n_{ijk} is the count of new firms in district j, industry k; d_{ijk} are industry dummies; Z_{ijk} includes localisation economies (σ_{jk}), inter-industry linkages (Λ_{kj}), urbanisation (U_j), market access (MA_j), education (Ed_j), infrastructure (X_j), wages (W_j), and wealth (WE_j)
- **Identification strategy:** Instrumental variable approach using historical land revenue institutions (Zamindari, Ryotwari, Mahalwari systems) as instruments for potentially endogenous agglomeration variables; exploits exogenous historical variation in colonial-era land tenure systems
- **Key assumptions:** Count data generating process (Poisson/NB); IIA (addressed by equivalence between conditional logit and Poisson); instrument validity (historical land revenue institutions affect current firm location only through their effect on institutional quality/agglomeration); pre-determined explanatory variables (lagged one period)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| NSSO 62nd Round (Unorganised Manufacturing) | NSSO 73rd Round (2015–16) or ASUSE annual surveys (2021–22 onwards) | MoSPI unit-level data |
| NSSO 57th Round (Unorganised Services) | NSSO 73rd Round or ASUSE | MoSPI unit-level data |
| NSSO Employment-Unemployment Survey | Periodic Labour Force Survey (PLFS) | MoSPI PLFS unit-level data |
| Census 2001 population data | Census 2011 or projected population | Census of India |
| National Input-Output Table | Updated I-O Tables | CSO/MoSPI Supply-Use and I-O Tables (2017–18) |

#### 5.2 Suggested Variable Mapping
- Count of new firms → Enterprises reporting "operated for less than 3 years" in NSSO/ASUSE surveys
- Localisation economies → Sector-specific employment share by district from PLFS
- Inter-industry linkages → Constructed from I-O tables and district employment data
- Market access → Gravity model using Census district population and inter-district distances
- Infrastructure → Census/PLFS data on electrification and telecom access
- Historical instruments → District-level land revenue institution data (Banerjee and Iyer 2005)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain unit-level data from NSSO unorganised enterprise surveys and PLFS; acquire I-O tables and Census district-level data; compile historical land revenue data by district.
2. **Data cleaning:** Aggregate enterprise-level data to district-industry level (NIC 2-digit); identify new firms (operated <3 years); merge with district-level explanatory variables from PLFS and Census.
3. **Variable construction:** Compute localisation economies, I-O weighted inter-industry linkages, Herfindahl diversity index, gravity-based market access, education shares, infrastructure variables, and wealth indicators at the district level.
4. **Econometric estimation:** Estimate Poisson, Negative Binomial, ZIP, and Hurdle models; include industry fixed effects; run IV-Poisson using historical land revenue institutions.
5. **Robustness checks:** Compare manufacturing vs. services; vary model specifications (Poisson vs. NB vs. ZIP); test instrument validity (overidentification tests, first-stage F-statistics); restrict to subsamples by firm size.

#### 5.4 Potential Challenges in Indian Replication
- Constructing district-level I-O weighted linkage measures requires matching NIC codes across I-O tables and survey data
- Historical land revenue institution data must be compiled at the district level; boundary changes across censuses complicate mapping
- Identifying "new firms" requires the specific survey question about enterprise duration, which may differ across rounds
- Over-dispersion diagnostics and model selection across count models require careful implementation

### 6. Replication Difficulty Level
**Hard** — The study involves complex data construction (I-O linkages, market access, historical instruments) from multiple sources at the district-industry level, along with specialized count models and IV estimation.

### 7. Recommended for Student Replication?
**With caution** — Suitable for advanced graduate students with strong skills in spatial economics, count data models, and multi-source data construction; not recommended for introductory-level replication.

---

## Paper 25: R&D Strategy of Small and Medium Enterprises in India: Trends and Determinants

### 1. Citation
* **Authors:** Jaya Prakash Pradhan
* **Year:** 2010
* **Journal/Working Paper:** MPRA Paper No. 20951, Munich Personal RePEc Archive; Sardar Patel Institute of Economic & Social Research (SPIESR), Ahmedabad
* **DOI/Link:** https://mpra.ub.uni-muenchen.de/20951/

### 2. Abstract (Concise Summary)
This paper analyzes trends and determinants of in-house R&D investment by Indian manufacturing SMEs during 1991–2008. Using the Prowess database (CMIE), the author documents that Indian SMEs have the lowest incidence of R&D among firm size categories, and their R&D intensities have declined in the 2000s relative to the 1990s. However, among the sub-sample of SMEs that do engage in R&D, intensities are actually higher than those of large firms. The determinants of R&D intensity are estimated using a three-step Censored Quantile Regression (CQR) approach, which is robust to non-normal, heteroscedastic errors. Key findings include positive effects of firm age, firm size (with an inverted-U relationship), export orientation, raw material imports, business group affiliation, foreign firm affiliation, profit margins, sectoral R&D intensity, and competitive pressure from foreign investment and imports on SME R&D intensity.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Prowess Database, Centre for Monitoring Indian Economy (CMIE, 2009); OECD Bilateral Trade Database; Annual Survey of Industries (ASI) |
| Time Period | 1991–2008 |
| Unit of Analysis | Manufacturing firm (SME defined as per MSMED Act 2006: small ≤ Rs. 5 crore in plant & machinery; medium Rs. 5–10 crore) |
| Sample Size | 4,071 Indian manufacturing SMEs (unbalanced panel); CQR estimation: 16,724 observations for SMEs, 25,189 for large firms |
| Key Variables | Dependent: R&D intensity (R&D expenditure/sales %). Independent: Firm age (FAGE), firm size (FSIZE, FSIZE²), external technology purchase (ETP1: royalty/technical fees; ETP2: capital goods imports), export intensity (EX), raw material imports (RMI), foreign firm affiliation (AFF), business group affiliation (BGA), profit margin (PM), sectoral R&D intensity (IRD), Herfindahl index (HI), competition from FDI (CFI), import competition (IMP), fiscal benefits (FSB) |

### 4. Econometric Methodology
- **Model type:** Three-step Censored Quantile Regression (CQR) following Chernozhukov and Hong (2002)
- **Main estimating equation:**
  RDINT_{it} = β₀ + β₁·FAGE_{it-1} + β₂·FSIZE_{it-1} + β₃·FSIZE²_{it-1} + β₄·ETP1_{it-1} + β₅·ETP2_{it-1} + β₆·EX_{it-1} + β₇·RMI_{it-1} + β₈·AFF_i + β₉·BGA_i + β₁₀·PM_{it-1} + β₁₁·IRD_{jt} + β₁₂·HI_{jt} + β₁₃·CFI_{jt} + β₁₄·IMP_{jt} + β₁₅·FSB_{it-1} + ε_{it}
- **Identification strategy:** Lagged firm-specific explanatory variables (by one year) to mitigate simultaneity bias; separate estimation for SMEs and large firms for comparison; CQR at the 95th percentile quantile for SMEs (due to extreme censoring with <10% of SMEs reporting R&D)
- **Key assumptions:** CQR is robust to heteroscedastic, non-normal errors (Tobit rejected based on Skeels-Vella conditional moment test); censoring at zero is the appropriate data-generating process; one-year lag eliminates simultaneity; three-step CQR algorithm handles heavy censoring

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| Prowess Database (CMIE, 2009) | Prowess IQ (CMIE, latest version) | CMIE Prowess IQ (updated annually) |
| OECD Bilateral Trade Database | UN Comtrade / WITS | World Bank WITS or DGCIS trade data |
| Annual Survey of Industries | ASI (updated rounds) | MoSPI ASI unit-level data |

#### 5.2 Suggested Variable Mapping
- R&D intensity → R&D expenditure / Net sales (available in Prowess IQ)
- Firm size (MSMED definition) → Investment in plant & machinery from Prowess IQ
- External technology purchase → Royalty payments, technical fees, capital goods imports from Prowess
- Business group / Foreign affiliation → Ownership classification in Prowess
- Import competition → Import/domestic demand ratios from WITS and ASI production data
- Fiscal benefits → Tax deductions/benefits reported in Prowess

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Extract firm-level data from Prowess IQ for manufacturing firms (2010–2023); classify firms into SMEs and large based on MSMED Act criteria; obtain industry-level trade data from WITS/DGCIS and production data from ASI.
2. **Data cleaning:** Construct unbalanced panel; classify firms by ownership (standalone, group-affiliated, foreign, public); compute industry-level concentration (Herfindahl) and foreign firm shares.
3. **Variable construction:** Compute R&D intensity, export intensity, import ratios, external technology purchase variables; lag all firm-specific variables by one year; construct industry-level variables.
4. **Econometric estimation:** Implement three-step CQR (Chernozhukov-Hong algorithm): Step 1 — estimate logit for P(R&D>0); Step 2 — quantile regression on trimmed subsample; Step 3 — final quantile regression with bootstrap standard errors (1,000 replications). Estimate separately for SMEs and large firms at appropriate quantiles.
5. **Robustness checks:** Compare CQR results with Tobit ML estimates; vary quantile levels (75th, 90th, 95th percentile); test for sensitivity to SME definition thresholds; conduct sub-period analysis.

#### 5.4 Potential Challenges in Indian Replication
- Prowess IQ coverage of small firms may be incomplete; many SMEs are unlisted and may not report to databases
- MSMED Act definition thresholds have been revised (2020 revision uses investment + turnover criteria); mapping older definitions to current ones requires care
- The three-step CQR estimation is computationally demanding and requires specialized STATA code (or R equivalent)
- Heavy censoring (>90% of SMEs report zero R&D) creates challenges for quantile regression convergence

### 6. Replication Difficulty Level
**Moderate to Hard** — The CQR methodology is non-standard and computationally intensive; data construction from multiple sources (Prowess, WITS, ASI) adds complexity; but the empirical framework is well-documented.

### 7. Recommended for Student Replication?
**With caution** — Suitable for advanced students familiar with censored regression and quantile regression methods; the descriptive analysis and Tobit specification can serve as a simpler alternative entry point.

---

## Paper 26: Innovation and Employment: A Study of Indian Manufacturing Sector

### 1. Citation
* **Authors:** Swati Mehta
* **Year:** 2016
* **Journal/Working Paper:** Millennial Asia, Vol. 7(2), pp. 184–206; SAGE Publications
* **DOI/Link:** DOI: 10.1177/0976399616655032

### 2. Abstract (Concise Summary)
This paper examines the impact of innovation — both product and process — on employment in the Indian manufacturing sector. Using firm-level panel data from four industries of different technological intensity (pharmaceuticals as high-tech, transport as medium-high-tech, ferrous metals as medium-low-tech, and textiles as low-tech) over 2000–01 to 2013–14, the author employs Generalized Least Squares (GLS) panel regression controlling for heteroscedasticity and autocorrelation. Product innovation (proxied by expenditure on R&D, royalties, and technical fees) is found to have a significant positive effect on employment across all four industries, regardless of technology intensity. Process innovation (proxied by efficiency in use of assets) does not show a significant effect. The paper argues for building a "system of innovation" that encourages product (radical) innovations for long-term growth and employment.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | CMIE Prowess Database; ASI (Annual Survey of Industries) for industry-level trends |
| Time Period | 2000–01 to 2013–14 |
| Unit of Analysis | Manufacturing firm |
| Sample Size | Pharmaceuticals: 238 obs.; Transport: 420 obs.; Ferrous metals: 294 obs.; Textiles: 252 obs. (firm-year observations) |
| Key Variables | Dependent: ln(Employment). Independent: ln(Product development expenditure) — includes R&D, royalties, technical fees; ln(Efficiency in use of assets) — proxy for process innovation; ln(Sales); ln(Capital stock) |

### 4. Econometric Methodology
- **Model type:** Panel data Generalized Least Squares (GLS) regression, corrected for heteroscedasticity and serial autocorrelation
- **Main estimating equations:**
  - Model 1: ln(emp) = β₁·ln(proddev) + β₂·ln(efficiency) + constant + ε
  - Model 2: ln(emp) = β₁·ln(sales) + β₂·ln(capital stock) + β₃·ln(proddev) + β₄·ln(efficiency) + constant + ε
  - Estimated separately for each of the four technology-intensive industries
- **Identification strategy:** Panel variation across firms within each industry; GLS addresses heteroscedasticity (Breusch-Pagan test) and serial autocorrelation; AR(1) coefficient estimated; Wald χ² used for overall model significance
- **Key assumptions:** Correct functional form (log-log); GLS addresses heteroscedasticity and autocorrelation; "efficiency in use of assets" adequately proxies process innovation; product development expenditure captures product innovation; no severe multicollinearity (checked via correlation matrices)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| CMIE Prowess | CMIE Prowess IQ (latest version) | Same database, updated |
| ASI (industry-level trends) | ASI (latest rounds) | MoSPI ASI data |

#### 5.2 Suggested Variable Mapping
- Employment → Number of employees (available in Prowess IQ)
- Product development expenditure → R&D expenses + Royalty + Technical know-how fees (Prowess IQ)
- Efficiency in use of assets → Sales/Total assets or Asset turnover ratio (Prowess IQ)
- Sales, Capital stock → Directly available in Prowess IQ
- Technology classification → OECD classification of manufacturing industries by technology intensity

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Extract firm-level panel data from Prowess IQ for firms in pharmaceuticals, transport equipment, ferrous metals, and textiles (2014–2023); collect employment, sales, capital stock, and product development expenditure variables.
2. **Data cleaning:** Construct balanced or unbalanced panels for each industry; handle missing values; compute log transformations.
3. **Variable construction:** Compute ln(employment), ln(product development expenditure), ln(efficiency = sales/total assets), ln(sales), ln(capital stock); generate correlation matrices and summary statistics.
4. **Econometric estimation:** Estimate GLS models (xtgls in Stata) for each industry separately, correcting for heteroscedasticity and AR(1) autocorrelation; report Wald χ² statistics.
5. **Robustness checks:** Use alternative proxies for process innovation (e.g., capital intensity change); estimate using fixed effects and random effects models for comparison; include additional controls (firm age, export intensity); test for cross-industry pooled estimation.

#### 5.4 Potential Challenges in Indian Replication
- The proxy for process innovation ("efficiency in use of assets") is crude and may not capture true process innovation
- Product development expenditure conflates R&D with technology payments (royalties), which represent different innovation activities
- Sample sizes per industry are relatively small; extending the time period would help
- GLS without firm fixed effects may not adequately control for unobserved firm heterogeneity

### 6. Replication Difficulty Level
**Easy** — Standard panel data GLS regression with readily available Prowess data; straightforward variable construction.

### 7. Recommended for Student Replication?
**Yes** — Excellent introductory exercise in panel data econometrics; students can compare GLS with fixed effects/random effects and explore innovation-employment dynamics across industries.

---

## Paper 27: Formal Sector Subcontracting and Informal Sector Employment in Indian Manufacturing

### 1. Citation
* **Authors:** Ana I. Moreno-Monroy, Janneke Pieters, Abdul A. Erumban
* **Year:** 2014
* **Journal/Working Paper:** IZA Journal of Labor & Development, Vol. 3, Article 22 (Open Access)
* **DOI/Link:** http://www.izajold.com/content/3/1/22

### 2. Abstract (Concise Summary)
This paper investigates the link between formal sector subcontracting and informal sector employment in Indian manufacturing during 1995–2006. A key novelty is distinguishing between "modern" and "traditional" segments of the informal sector using a continuous, multi-dimensional modernity index based on capital-labor ratio, enterprise location, hired workers, and technical qualifications of owners. Using a state-industry panel constructed from nationally representative data (ASI for formal sector, NSS for informal sector), the authors estimate fixed-effects models and find that formal sector subcontracting is positively associated with employment growth only in the most modern segments of the informal sector. Increased subcontracting cannot explain persistently high employment in traditional informal manufacturing. These findings support the "modernization view" of informal-formal linkages.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (17 major states) |
| Data Source | Annual Survey of Industries (ASI) for formal sector; National Sample Survey (NSS) of Unorganized Manufacturing for informal sector |
| Time Period | 1994–95, 2000–01, 2005–06 (three time points) |
| Unit of Analysis | State-industry (2-digit NIC industry × 17 states) |
| Sample Size | 774 state-industry-year observations (up to 258 per year, 21 industries × 17 states, minus missing) |
| Key Variables | Dependent: ln(informal sector employment), ln(hired workers), ln(wage bill). Independent: ln(formal sector subcontracting value), modernity index (composite of capital-labor ratio, location, hired workers, qualified owner), ln(formal sector employment). Fixed effects: state-industry (α_{is}), state-time (γ_{st}), industry-time (δ_{it}) |

### 4. Econometric Methodology
- **Model type:** Panel fixed effects model (state-industry fixed effects, state-time dummies, industry-time dummies)
- **Main estimating equation:**
  ln(Y_{ist}) = α_{is} + γ_{st} + δ_{it} + β₁·ln(FS_{ist}) + β₂·ln(FS_{ist})·M^{95}_{is} + β₃·M^{95}_{is}·I_{01} + β₄·M^{95}_{is}·I_{06} + β₅·ln(empF_{ist}) + ε_{ist}
  where Y is informal employment/hired workers/wage bill; FS is formal sector subcontracting value; M^{95} is the start-of-period modernity index; I_{01}, I_{06} are year dummies
- **Identification strategy:** Within state-industry variation over three time periods; state-time and industry-time dummies absorb state-specific trends (e.g., labor regulation changes) and industry-specific trends (e.g., tariff changes); modernity index measured at start of period (1995) to avoid reverse causality on modernity itself
- **Key assumptions:** No time-varying unobservables correlated with both subcontracting and informal employment after controlling for state-time and industry-time trends; modernity index is pre-determined; authors acknowledge inability to instrument for causal identification but argue reverse causality also implies production linkages

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI (1994–95, 2000–01, 2005–06) | ASI (2005–06, 2010–11, 2015–16, 2020–21) | MoSPI ASI unit-level data |
| NSS Unorganized Manufacturing (same years) | NSS 62nd Round (2005–06), 67th Round (2010–11), 73rd Round (2015–16), ASUSE (2021–22 onwards) | MoSPI NSS/ASUSE unit-level data |

#### 5.2 Suggested Variable Mapping
- Formal sector subcontracting → ASI variable: "Purchase value of goods sold in same condition" + "Cost of contract and commission work done by others" (available in ASI factory-level data)
- Informal employment → Total workers in unorganised manufacturing from NSS/ASUSE
- Hired workers → Hired workers (excluding owners and family workers) in NSS/ASUSE
- Wage bill → Total compensation paid to hired workers in NSS/ASUSE
- Modernity index → Construct from start-of-period: (i) log capital per worker, (ii) share of enterprises outside household, (iii) average hired workers per enterprise, (iv) share with technically qualified owner; standardize and average

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain unit-level ASI and NSS/ASUSE data for at least three time points; identify state and NIC 2-digit codes consistently across rounds.
2. **Data cleaning:** Aggregate ASI factory-level data to state-industry level; compute subcontracting values; aggregate NSS/ASUSE data to state-industry level for employment, hired workers, and wage bills; deflate monetary variables using state-industry specific WPI.
3. **Variable construction:** Construct modernity index from start-of-period NSS data (standardize each component across state-industries, take simple average); compute interaction terms with subcontracting; construct formal sector employment controls.
4. **Econometric estimation:** Estimate panel FE model with state-industry, state-year, and industry-year fixed effects; test both continuous modernity interaction and quartile-based specifications; cluster standard errors at the state-industry level.
5. **Robustness checks:** Vary modernity index components (exclude technical qualification if unavailable); use 3-component index; test with different time periods; check sensitivity to WPI deflator choice; test for alternative segment boundaries.

#### 5.4 Potential Challenges in Indian Replication
- Matching NIC codes across ASI and NSS survey rounds requires concordance tables due to NIC revisions (1998, 2004, 2008)
- ASI subcontracting variables may be recorded differently across rounds
- Constructing a consistent modernity index requires the "technical qualification of proprietor" variable, which may not be available in all NSS rounds
- State boundary changes (e.g., creation of Jharkhand, Chhattisgarh, Uttarakhand) complicate panel construction

### 6. Replication Difficulty Level
**Moderate** — The methodology (panel FE) is standard, but data construction from two large nationally representative surveys at the state-industry level requires substantial data processing; concordance across NIC codes and survey rounds adds complexity.

### 7. Recommended for Student Replication?
**Yes** — Highly recommended for graduate students interested in formal-informal sector linkages; the panel fixed effects methodology is standard and the research question is highly relevant.

---

## Paper 28: Sub-Contracting and Efficiency of the Informal Sector in India

### 1. Citation
* **Authors:** Indrajit Bairagya
* **Year:** 2013
* **Journal/Working Paper:** The Journal of Developing Areas, Vol. 47, No. 2, Fall 2013
* **DOI/Link:** Project MUSE (https://muse.jhu.edu/article/503598)

### 2. Abstract (Concise Summary)
This paper examines the technical efficiency of informal sector enterprises in India and tests whether firms operating on contracts with formal firms/agencies are more efficient than non-contracting firms. Using unit-level data from the NSSO 55th Round (1999–2000) enterprise survey, the author applies a two-stage Data Envelopment Analysis (DEA) approach. In the first stage, output-oriented technical efficiency scores are computed. In the second stage, a Tobit censored regression identifies determinants of inefficiency. The analysis is conducted separately for Delhi (a developed state) and Orissa (an underdeveloped state). Key findings are that firms on contracts are less efficient in Delhi but more efficient in Orissa. Additionally, enforcement of regulations makes firms more inefficient in both states, raising questions about the wisdom of formalizing the informal sector through regulation.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India — Delhi (developed state) and Orissa (underdeveloped state) |
| Data Source | NSSO 55th Round (1999–2000) Enterprise Survey — Non-Agricultural Informal Sector |
| Time Period | 1999–2000 |
| Unit of Analysis | Informal enterprise |
| Sample Size | Delhi: 1,689 enterprises; Orissa: 3,000 enterprises (after removing outliers); 32 states/UTs for cross-state comparison |
| Key Variables | Output: Gross Value Added (GVA). Inputs: Capital (gross fixed assets), Labour (number of workers). Determinants of efficiency: Interest cost on loans, nature of operation (perennial/seasonal/casual), problems faced (lack of market/competition), contracting status (dummy), enterprise size (large dummy), registration status (registered dummy), location (within household premises dummy) |

### 4. Econometric Methodology
- **Model type:** Two-stage Data Envelopment Analysis (DEA)
- **Stage 1 — DEA (output-oriented, VRS):**
  Max Φ subject to: Σλ_i·A_i ≥ Φ·A_i; Σλ_i·C_i ≤ C_i; Σλ_i·L_i ≤ L_i; Σλ_i = 1; λ_i ≥ 0
  where A = GVA, C = Capital, L = Labour; 1/Φ = technical efficiency score
- **Stage 2 — Tobit censored regression:**
  y_i* = β·x_i + ε_i; y_i = y_i* if y_i* > 0, y_i = 0 otherwise
  where y_i = (1 − TE_i) is the inefficiency score; x_i includes loan interest, perennial dummy, lack of market dummy, contracting dummy, large firm dummy, registration dummy, household location dummy
- **Identification strategy:** Cross-sectional comparison between enterprises within each state; two-stage approach where DEA efficiency scores (first stage) are explained by firm characteristics (second stage); separate estimation for developed (Delhi) vs. underdeveloped (Orissa) states
- **Key assumptions:** DEA assumes all deviations from frontier reflect inefficiency (no random noise); VRS (variable returns to scale) assumption; Tobit assumes censoring at zero is appropriate; contextual variables are independent of input variables (Banker and Natarajan 2008)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| NSSO 55th Round (1999–2000) Enterprise Survey | NSSO 73rd Round (2015–16) or ASUSE (2021–22 onwards) | MoSPI unit-level data |

#### 5.2 Suggested Variable Mapping
- GVA → Annual receipts minus expenses (available in NSS/ASUSE enterprise surveys)
- Capital (Gross fixed assets) → Market value of owned/hired fixed assets (land, building, plant & machinery, transport, other)
- Labour → Total workers (working owner + hired + family helpers)
- Contracting status → Whether enterprise operates on contract basis (available in NSS enterprise surveys)
- Registration status → Whether registered under any act/authority
- Enterprise location → Within household premises vs. outside
- Enterprise type → OAE vs. establishment
- Nature of operation → Perennial, seasonal, casual (available in NSS surveys)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Obtain unit-level enterprise data from NSSO 73rd Round (2015–16) or ASUSE; select two contrasting states (e.g., Delhi vs. Bihar or Odisha for developed vs. underdeveloped comparison).
2. **Data cleaning:** Remove outliers; filter for non-agricultural informal enterprises; classify by sub-sector (manufacturing, construction, trade, hotels, transport, other services).
3. **Variable construction:** Compute GVA, capital stock, and worker counts; create dummy variables for contracting status, registration, location, enterprise size, and nature of operation; compute GVA per worker for descriptive analysis.
4. **Econometric estimation:** Stage 1 — Run output-oriented DEA with VRS using DEAP software or R/Stata DEA packages; compute efficiency scores. Stage 2 — Transform efficiency to inefficiency (1−TE); estimate Tobit regression of inefficiency on explanatory variables, separately for each state.
5. **Robustness checks:** Compare VRS and CRS efficiency scores; test sensitivity to outlier treatment; use Stochastic Frontier Analysis (SFA) as an alternative to DEA; extend to more states for cross-state comparisons; use truncated regression (Simar-Wilson bootstrap) instead of Tobit for second-stage.

#### 5.4 Potential Challenges in Indian Replication
- DEA results are sensitive to outliers; careful data cleaning is essential
- The assumption that all deviation from the frontier is inefficiency (no random noise) is strong; SFA would provide a stochastic alternative
- Comparing efficiency scores across states estimated on separate frontiers requires caution (as the author notes, inter-state comparisons are not direct)
- The contracting variable may be coded differently across NSS rounds; consistency must be verified
- Two-stage DEA-Tobit has been criticized in the efficiency literature (Simar and Wilson 2007); bootstrap methods may be preferred

### 6. Replication Difficulty Level
**Moderate** — DEA is conceptually straightforward but requires specialized software; the Tobit second stage is standard. The main challenge is careful data processing and awareness of DEA limitations.

### 7. Recommended for Student Replication?
**Yes** — Good introduction to non-parametric efficiency analysis (DEA) and its application to India's informal sector; students can learn both DEA and Tobit regression while addressing a policy-relevant question about subcontracting and formalization.

---
---

## Paper 29: Firms' R&D Activities in Indian Organised Manufacturing Sector: Are Tech-SMEs Different?

### 1. Citation
* **Authors:** Shailender Kumar Hooda
* **Year:** 2024
* **Journal/Working Paper:** ISID Working Paper No. 285, Institute for Studies in Industrial Development, New Delhi
* **DOI/Link:** https://isid.org.in

### 2. Abstract (Concise Summary)
This study investigates firm-level R&D investment behaviour in India's organised manufacturing sector using nationally representative unit-level data from the Annual Survey of Industries (ASI) for the period 2015-16 to 2021-22. The paper distinguishes R&D propensity and intensity across small-and-medium-size (SMS) and large firms, and across technology-intensity classifications. Using the Cragg double-hurdle model and the Heckman selection model, it examines determinants of R&D engagement and expenditure, incorporating novel variables such as product-subsidy reception and industrial concentration. Key findings indicate that while aggregate R&D spending is rising, R&D intensity shows a declining trend. SMS firms exhibit higher R&D intensity than large firms in both low- and high-tech sectors, though the pandemic has eroded this advantage. Larger firms, those with foreign capital, and high-tech industry affiliation are more likely to engage in and spend more on R&D. Product subsidies show limited direct impact on R&D engagement likelihood, though firms receiving subsidies on a larger number of products show significantly positive effects.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (national) |
| Data Source | Annual Survey of Industries (ASI), unit-level data, CSO/MoSPI |
| Time Period | 2015-16 to 2021-22 |
| Unit of Analysis | Factory/firm (registered manufacturing units) |
| Sample Size | All ASI census and sample factories (nationally representative; exact N varies by year) |
| Key Variables | R&D dummy (whether firm has R&D unit), R&D expenditure, firm age, firm size (number of employees), foreign capital share, imported input technology share, profit-GVA share, GVA, skill intensity, technology level of industry (NIC 3-digit based), high-industrial-activity state dummy, product subsidy dummy and count |

### 4. Econometric Methodology
- **Model type:** Cragg double-hurdle model (panel variant using `xtdhreg` in Stata) and Heckman two-stage selection model
- **Main estimating equations:**
  - Stage 1 (Probit – likelihood of R&D engagement): RDD_it = α₀ + β₁AGE + β₂AGE² + β₃SIZE + β₄FCS + β₅MIT + β₆PGS + β₇lnGVA + β₈SKILL + β₉TLI + β₁₀HIS + β₁₁PS + ε_it
  - Stage 2 (Truncated regression – extent of R&D spending): lnRD_it = α₀ + β₁AGE + β₂AGE² + β₃SIZE + β₄FCS + β₅MIT + β₆PGS + β₇lnGVA + β₈SKILL + β₉TLI + β₁₀HIS + β₁₁PS + ε_it
- **Identification strategy:** Two-stage modelling separates the participation decision from the expenditure decision; Heckman model corrects for sample selection bias via inverse Mills ratio; Cragg model treats zero R&D as reported (not missing)
- **Key assumptions:** Constant returns to scale implicit in GVA-based normalisation; firm-level unobserved heterogeneity addressed via panel hurdle model; technology-intensity classification follows Pavitt (1984) and Czarnitzki & Thorwarth (2012)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI unit-level data (2015-16 to 2021-22) | Same source – extend to latest available year | ASI microdata via MoSPI (apply through official channel) |
| NIC 3-digit industry classification | Same classification | NIC-2008 / NIC-2004 concordance tables from CSO |
| Product subsidy data (Block-J of ASI) | Same source | ASI schedule Block-J (available from 2015-16 onwards) |

#### 5.2 Suggested Variable Mapping
- RDD → Binary: 1 if R&D expenditure > 0 (ASI schedule)
- lnRD → Log of R&D expenditure (ASI Block on R&D, available from 2015-16)
- SIZE → Log of total persons engaged
- AGE → Current year minus year of initial production
- FCS → Dummy for foreign share capital presence (ASI)
- MIT → Imported inputs / total inputs
- PGS → Profit / GVA
- SKILL → Supervisory & managerial staff / total persons engaged
- TLI → 0/1 based on NIC 3-digit technology classification
- HIS → Dummy for states with >5% share in national manufacturing sales/units
- PS → Dummy for product subsidy receipt (Block-J)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Apply to MoSPI for ASI unit-level microdata (2015-16 to 2021-22 or latest). Obtain NIC concordance tables.
2. **Data cleaning:** Drop Joint Return (JR) units and factories with zero fixed assets (as per author's protocol). Handle census vs. sample strata using multipliers.
3. **Variable construction:** Construct R&D dummy and log R&D expenditure; compute technology-intensity classification at NIC 3-digit using OECD/Pavitt taxonomy; compute HIS dummy based on state-level share thresholds; create product subsidy variables from Block-J.
4. **Econometric estimation:** Estimate Cragg double-hurdle model using `xtdhreg` (Engel & Moffatt, 2014) in Stata-16+. Estimate Heckman two-stage model with inverse Mills ratio correction. Run separate regressions for SMS vs. large firms and by technology intensity.
5. **Robustness checks:** Replace product subsidy dummy with count of subsidised products; run separate models for DST/DBT-registered vs. unregistered firms; split sample by pre-/post-pandemic years (2019-20 as breakpoint).

#### 5.4 Potential Challenges in Indian Replication
- ASI microdata access requires formal application and may involve delays
- R&D data in ASI is only available from 2015-16 onward, limiting time-series depth
- Joint Return scheme complicates unit-level identification
- Some variables (e.g., R&D stock, patent counts, foreign equity share detail) are not available in ASI
- Technology intensity classification at NIC 3-digit level requires careful manual mapping

### 6. Replication Difficulty Level
**Moderate** – The study uses the same ASI data that is the target for replication. The Cragg double-hurdle model requires specialised Stata commands (`xtdhreg`), and variable construction (technology classification, HIS identification) demands careful concordance work.

### 7. Recommended for Student Replication?
**Yes** – This paper is ideal for replication as it uses Indian ASI data with clearly specified models and Stata commands; students can extend the analysis to newer ASI rounds.

---

## Paper 30: The Determinants of R&D in the Indian Pharmaceutical Sector: A Firm Level Study of Outward Investors

### 1. Citation
* **Authors:** K. Narayanan and Ronny Thomas
* **Year:** ~2008 (working paper / conference paper)
* **Journal/Working Paper:** Working Paper, Department of Humanities and Social Sciences, Indian Institute of Technology Bombay
* **DOI/Link:** Contact: knn@iitb.ac.in

### 2. Abstract (Concise Summary)
This study identifies the determinants of R&D investment in the Indian pharmaceutical sector, with particular attention to the role of outward foreign direct investment (OFDI). Using an unbalanced panel of 173 pharmaceutical firms from 1990 to 2005 sourced from the CMIE Prowess database, the authors employ Probit and Tobit models to examine both the probability of undertaking R&D and R&D intensity. An inverted-U relationship between firm size and R&D is identified. Older firms, export-oriented firms, and those importing capital goods invest more in R&D. Outward investment by a firm reduces the probability of investing in R&D, suggesting a substitution effect. A sub-sample of outward-investing firms (390 observations) reveals that firm size, export intensity, and capital goods imports positively influence R&D decisions among internationalising firms.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | CMIE Prowess database |
| Time Period | 1990 to 2005 |
| Unit of Analysis | Firm (pharmaceutical sector) |
| Sample Size | Unbalanced panel of 173 firms; sub-sample of outward investors with 390 observations |
| Key Variables | R&D intensity (R&D/Sales×100), firm size (firm sales/industry sales), export intensity (exports/sales), capital goods import intensity, disembodied technology imports (royalties & technical fees/sales), rate of profit (PBDIT/sales), firm age, advertisement intensity (advt./sales), foreign ownership dummy (≥10% foreign equity) |

### 4. Econometric Methodology
- **Model type:** Probit model (for probability of R&D), Tobit model (for R&D intensity with censoring at zero), Fixed Effects and Random Effects panel models (for R&D-intensive firms sub-sample)
- **Main estimating equations:**
  - Probit: RDINT*_it = α + β₁SIZE + β₂SIZE² + β₃EXPINT + β₄IMPCINT + β₅IMPRPINT + β₆PBDIT + β₇AGE + β₈ADVINT + β₉FP + μ_it; RDINT = 1 if RDINT* > 0
  - Tobit: RDCINT*_it = α + β₁SIZE + β₂SIZE² + β₃EXPINT + β₄IMPCINT + β₅IMPRPINT + β₆PBDIT + β₇AGE + β₈ADVINT + β₉FP + μ_it; RDCINT = RDCINT* if > 0, else 0
- **Identification strategy:** Cross-sectional and panel variation in firm-specific characteristics; quadratic term for firm size to capture nonlinear relationship; marginal effects decomposed following Moffitt and McDonald (1980) for Tobit
- **Key assumptions:** Static panel data model – no correction for simultaneity between R&D and explanatory variables; Tobit assumes same process governs participation and intensity decisions; exogeneity of regressors acknowledged as limitation

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| CMIE Prowess (1990-2005) | Updated CMIE Prowess/ProwessIQ | CMIE ProwessIQ (subscription-based; available at many Indian universities) |
| Pharmaceutical firms identified via NIC codes | Same classification using NIC-2008 codes for pharma | NIC-2008: Division 21 (Pharmaceuticals) |

#### 5.2 Suggested Variable Mapping
- RDCINT → R&D expenditure / Net Sales × 100 (from Prowess)
- SIZE → Firm's net sales / total industry sales (deflated)
- EXPINT → Total exports / Net sales
- IMPCINT → Import of capital goods / Net sales
- IMPRPINT → Royalty and technical fees / Net sales
- PBDIT → Profit before depreciation, interest and tax / Net sales
- AGE → Current year − year of incorporation
- ADVINT → Advertisement expenditure / Net sales
- FP → Dummy: 1 if foreign equity ≥ 10%
- OFDI dummy → Constructed from RBI OFDI data or Prowess overseas investment fields

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Access CMIE ProwessIQ; filter firms by NIC pharmaceutical codes; extract panel data for extended period (e.g., 2005–2023).
2. **Data cleaning:** Handle missing observations for unbalanced panel; deflate sales variables using WPI (base year 2011-12); identify outward-investing firms from Prowess or RBI data on OFDI approvals.
3. **Variable construction:** Compute all intensity ratios; create quadratic term for firm size; construct foreign ownership dummy.
4. **Econometric estimation:** Run Probit for R&D participation, Tobit for R&D intensity (with marginal effects decomposition), and FE/RE models for R&D-active sub-sample. Run Hausman test for FE vs. RE selection.
5. **Robustness checks:** Extend to post-TRIPS patent regime (post-2005); compare pre- and post-2005 Patent Act amendment effects; use Heckman selection model as alternative to Tobit; add interaction terms for OFDI × firm size.

#### 5.4 Potential Challenges in Indian Replication
- Prowess database requires institutional subscription
- Identifying outward investment accurately requires supplementary data (RBI OFDI approvals or firm annual reports)
- Simultaneity bias between R&D and exports/profits is not addressed and remains a limitation
- Pharmaceutical industry has undergone significant structural changes post-2005 (TRIPS compliance), requiring careful period selection

### 6. Replication Difficulty Level
**Easy to Moderate** – Standard Probit/Tobit models on readily available Prowess data. The main complexity lies in correctly identifying outward-investing firms and handling the unbalanced panel.

### 7. Recommended for Student Replication?
**Yes** – Straightforward methodology with clearly defined variables; students can extend to post-TRIPS period to examine structural breaks in pharma R&D behaviour.

---

## Paper 31: International Trade and Productivity Growth: Evidence from the Organised Manufacturing Sector in India

### 1. Citation
* **Authors:** R. Rijesh
* **Year:** 2017
* **Journal/Working Paper:** ISID Working Paper No. 198, Institute for Studies in Industrial Development, New Delhi
* **DOI/Link:** http://isid.org.in

### 2. Abstract (Concise Summary)
This study examines the impact of international trade on manufacturing productivity in India using a balanced panel of 17 two-digit organised manufacturing industries over 1980–2013. Rather than using trade policy dummies, the author constructs ex-post trade variables—relative import price, import penetration ratio, and export intensity—to capture distinct theoretical channels (economies of scale, reallocation, competition, and spillover effects). Using random-effects panel estimation (selected via Hausman test), with FGLS as a robustness check, the study finds trade-induced productivity gains primarily channelled through imports, becoming prominent after 1–2 year lags. While exports show a positive association with productivity, the relationship is statistically significant only contemporaneously. The results underscore the dynamic rather than static nature of trade's impact on Indian manufacturing productivity.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | Annual Survey of Industries (ASI) Volume 1 for production data; UN Comtrade/WITS for trade data; WPI for deflators |
| Time Period | 1980-81 to 2013-14 |
| Unit of Analysis | 2-digit manufacturing industry (17 sectors) |
| Sample Size | Balanced panel: 17 industries × 34 years = 578 observations |
| Key Variables | Labour productivity (LP), Total Factor Productivity (TFP), relative import price, import penetration ratio, export intensity, capital intensity, capacity utilisation |

### 4. Econometric Methodology
- **Model type:** Panel regression – Fixed Effects (FE) and Random Effects (RE) estimation; Flexible Generalised Least Squares (FGLS) for robustness
- **Main estimating equation:**
  ΔlnP_jt = α_j + β_i·ΔRP_{t-i} + γ_i·ΔIMP_{t-i} + δ_i·ΔEXI_{t-i} + ϑ·ΔCI_t + θ·ΔCU_t + μ_t
  where P = TFP or LP; RP = relative import price; IMP = import penetration ratio; EXI = export intensity; CI = capital intensity; CU = capacity utilisation; i = 0, 1, or 2 (lag structure)
- **Identification strategy:** Ex-post trade variables (not policy dummies) capture actual trade exposure; lag structure (0, 1, 2 years) captures dynamic adjustment; Hausman test selects between FE and RE
- **Key assumptions:** Exogeneity of trade variables to productivity shocks at sectoral level; constant returns to scale in TFP construction; productivity measured via growth accounting (Tornqvist index)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| ASI Volume 1 (2-digit industry summaries) | Same source, extended to 2020-21 | ASI Summary Results, MoSPI (publicly available) |
| UN Comtrade / WITS trade data | Same source or DGCIS trade data | UN Comtrade / WITS (free access); DGCI&S (for India-specific) |
| WPI for deflation | Same source | Office of Economic Adviser, Ministry of Commerce |
| NIC concordance tables | Same | CSO/MoSPI NIC concordance documents |

#### 5.2 Suggested Variable Mapping
- LP → Real GVA per worker (from ASI)
- TFP → Tornqvist index residual from gross output growth accounting (KLEMS framework)
- Relative import price → Unit value of imports / domestic WPI (commodity-level matching)
- Import penetration ratio → Imports / (Domestic production + Imports − Exports)
- Export intensity → Exports / Domestic production
- Capital intensity → Real fixed capital stock per worker
- Capacity utilisation → Actual output / potential output (derived from capital-output trends)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Download ASI summary results (Volume 1) from MoSPI website for 1980-81 to latest year; download bilateral trade data from UN Comtrade at HS/SITC level; obtain WPI series from Office of Economic Adviser.
2. **Data cleaning:** Build NIC concordance across NIC-1987, NIC-1998, NIC-2004, and NIC-2008 for consistent 17-sector classification; deflate output and input series using appropriate WPI indices.
3. **Variable construction:** Compute TFP using gross output growth accounting (Tornqvist index); construct trade variables (relative import price requires matching commodity-level import unit values to domestic WPI); compute capacity utilisation proxy.
4. **Econometric estimation:** Estimate panel RE model (Equation 2) at contemporaneous and 1-year and 2-year lags; run Hausman test; estimate FGLS for robustness.
5. **Robustness checks:** Extend period to post-2013; split sample into pre- and post-reform sub-periods; use alternative TFP measures (e.g., Levinsohn-Petrin at firm level); add tariff data as instrument.

#### 5.4 Potential Challenges in Indian Replication
- NIC concordance across four classification revisions is technically demanding
- Constructing relative import price requires matching trade product classifications (HS/SITC) to domestic NIC industries
- Capacity utilisation is not directly observed and must be proxied
- ASI summary data are at aggregate level; unit-level data would require separate application
- Post-2011-12 NAS series uses different base year and sectoral classification

### 6. Replication Difficulty Level
**Moderate** – The econometric methods (panel RE/FE/FGLS) are standard, but the data construction—especially NIC concordance, TFP measurement, and trade variable matching—requires substantial effort.

### 7. Recommended for Student Replication?
**Yes, with caution** – Excellent pedagogical exercise in trade-productivity analysis, but the data concordance and variable construction phases are time-intensive and require familiarity with Indian industrial classification systems.

---

## Paper 32: Determinants of Innovation in Selected Manufacturing Firms in India: Role of R&D and Exports

### 1. Citation
* **Authors:** K. Seenaiah and Badri Narayan Rath
* **Year:** 2018
* **Journal/Working Paper:** *Science, Technology & Society*, Vol. 23, No. 1, pp. 65–84
* **DOI/Link:** DOI: 10.1177/0971721817744445

### 2. Abstract (Concise Summary)
This study examines the determinants of innovation in Indian manufacturing firms using a primary survey of 190 firms from Bengaluru and Hyderabad, combined with secondary data from the CMIE Prowess database for the period 2011–2013. Innovation is defined as a binary outcome capturing product, process, marketing, or organisational innovation. Using a panel probit model, the authors find that exports and R&D expenditure positively and significantly drive innovation. Import intensity, manager's prior foreign-firm experience, and employee training also positively affect innovation. However, firm age and capital intensity have negative effects. A sub-sample analysis of capital-intensive firms is also conducted. The findings underline the importance of export orientation and R&D subsidies for boosting innovation in Indian manufacturing.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India (Bengaluru and Hyderabad cities) |
| Data Source | Primary survey (innovation data) + CMIE Prowess database (financial variables) |
| Time Period | 2011 to 2013 |
| Unit of Analysis | Firm (manufacturing, listed on BSE) |
| Sample Size | 190 firms × 3 years = 570 observations |
| Key Variables | Innovation (binary: product/process/marketing/organisational), firm age, firm size (real sales/real GFA), capital intensity (GFA/employees), export intensity (exports/sales), import intensity (imports/sales), R&D dummy, manager's education (engineering/technical = 1), manager's experience (foreign firm = 1), training to employees (dummy) |

### 4. Econometric Methodology
- **Model type:** Panel probit regression model (maximum likelihood estimation), corrected for heteroscedasticity
- **Main estimating equation:**
  INV_it = β₀ + β₁AGE_it + β₂SIZE_it + β₃CI_it + β₄EXI_it + β₅IMI_it + β₆RD_it + β₇MEDU_it + β₈MEXP_it + β₉TRN_it + ε_it
  where INV = 1 if firm engages in any innovation, 0 otherwise
- **Identification strategy:** Cross-sectional and temporal variation across 190 firms over 3 years; marginal effects computed separately; three alternative model specifications to address potential multicollinearity
- **Key assumptions:** Innovation is exogenously determined by firm-level characteristics; no endogeneity correction; purposive (non-random) sampling from BSE-listed firms in two cities

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| Primary innovation survey (190 firms, Bengaluru & Hyderabad) | National Innovation Survey or new primary survey | DST National Innovation Survey (2011, 2014); or conduct fresh primary survey |
| CMIE Prowess (financial data) | Updated CMIE ProwessIQ | CMIE ProwessIQ database |

#### 5.2 Suggested Variable Mapping
- INV → Binary innovation indicator (from survey or patent/trademark data)
- AGE → Current year − year of establishment
- SIZE → Real net sales / Real gross fixed assets
- CI → Gross fixed assets / Number of employees
- EXI → Total exports / Total sales
- IMI → Total imports / Total sales
- RD → Dummy: 1 if firm reports R&D expenditure > 0
- Manager-related variables → Require primary survey data
- TRN → Dummy for employee training programs (from survey)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Access CMIE ProwessIQ for financial variables of BSE-listed manufacturing firms; obtain innovation-related data via primary survey (structured questionnaire based on Oslo Manual guidelines) or use the DST National Innovation Survey.
2. **Data cleaning:** Match primary survey data with Prowess financial data by company identifier; construct balanced/unbalanced panel for the survey period.
3. **Variable construction:** Code innovation as binary (any product/process/marketing/organisational innovation); compute all intensity ratios from Prowess data; code binary manager and training variables from survey responses.
4. **Econometric estimation:** Estimate panel probit model using maximum likelihood; compute marginal effects; run three specifications (reduced and full models) to check multicollinearity sensitivity.
5. **Robustness checks:** Estimate logit model as alternative; run separate models for capital-intensive vs. labour-intensive firms; explore ordered probit if innovation intensity data available; use Heckman probit to address potential sample selection.

#### 5.4 Potential Challenges in Indian Replication
- Innovation data is not available in standard secondary databases; requires primary survey or use of limited DST National Innovation Survey data
- Purposive sampling from two cities limits external validity
- Small sample size (190 firms) may limit statistical power
- Manager-level variables (education, foreign experience) require firm-level primary data collection
- BSE-listed firms are not representative of the broader manufacturing sector

### 6. Replication Difficulty Level
**Hard** – The primary survey component is resource-intensive; innovation data is not readily available in Indian secondary databases; the small, geographically concentrated sample limits generalisability.

### 7. Recommended for Student Replication?
**With caution** – The econometric model is straightforward (panel probit), but the reliance on primary survey data makes full replication challenging; students could replicate using DST National Innovation Survey data if accessible, or adapt the approach to a new city-based sample.

---

## Paper 33: Technological Capabilities and Exports: Evidence from Indian Manufacturing Firms

### 1. Citation
* **Authors:** Smruti Ranjan Sahoo, Krishnapriya Vadakoot Sathees, and Anurag Anand
* **Year:** 2025
* **Journal/Working Paper:** CRIT/CWS Working Paper Series No. 89, Centre for WTO Studies / Centre for Research in International Trade, Indian Institute of Foreign Trade, New Delhi
* **DOI/Link:** Not available (working paper)

### 2. Abstract (Concise Summary)
This paper examines the drivers behind the expansion of India's technology-intensive (high-technology and medium-high-technology) manufacturing exports from 2008 to 2020. Using an unbalanced panel of 2,334 firms and 21,718 observations from the CMIE Prowess database, the study argues that export performance is primarily attributable to firms' technological capability-building through in-house R&D, human capital investment (staff training), and absorption of imported foreign technologies (capital goods, raw material imports, royalty payments). Employing Quasi-Maximum Likelihood Estimation (QMLE) as the primary method—appropriate for the fractional nature of the dependent variable (export intensity bounded between 0 and 1)—and Tobit estimation for robustness, the study finds that firms investing in R&D, human resources, and imported technology exhibit significantly higher export intensity. Location-specific variables (patents in region, ease of doing business, access to finance) also matter. Industry-level disaggregated analysis provides scope for targeted policy implications.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | CMIE Prowess database (firm-level); RBI Handbook of Statistics on Indian States (state-level); DPIIT (patent data, ease of doing business scores); Office of Controller General of Patents |
| Time Period | 2008 to 2020 |
| Unit of Analysis | Firm (high-technology and medium-high-technology manufacturing, OECD classification) |
| Sample Size | 2,334 firms; 21,718 observations (unbalanced panel) |
| Key Variables | Export intensity (exports/sales), R&D intensity (R&D/sales), capital goods import intensity, raw material import intensity, royalty payment intensity, indigenous raw material intensity, advertisement & marketing intensity, outsourcing intensity, staff training intensity, MNE affiliation dummy (foreign equity >10%), firm age, firm size (log GFA), location-specific: state patents, knowledge-intensive firms count, ease of doing business rank, bank branches |

### 4. Econometric Methodology
- **Model type:** Quasi-Maximum Likelihood Estimation (QMLE) following Papke & Wooldridge (1996); Tobit model for robustness
- **Main estimating equation:**
  EXPINT_ft = α + β₁·Technological_ft + β₂·Firm_specific_ft + β₃·Location_specific_rt + ν_i + ξ_t + ε_ft
  where EXPINT = exports/sales (fractional, 0 ≤ EXPINT < 1); Technological = {RDINT, CGIINT, RMINT, RPINT}; Firm_specific = {INDRMINT, ADVINT, OUTINT, STINT, MNEs, AGE, SIZE}; Location = {PATENT, KFIRMS, EASE, BANK}; ν_i = industry dummies; ξ_t = time dummies
- **QMLE specification:** E(EXPINT|x) = G(xβ), where G(·) is a logistic cdf: G(·) = exp(·)/[1+exp(·)]
- **Identification strategy:** Exploits within-firm variation over time with industry and year fixed effects; QMLE handles fractional dependent variable without requiring ad-hoc data transformations
- **Key assumptions:** Conditional mean correctly specified as logistic function; exogeneity of regressors (no IV strategy); firms present at least thrice in panel; 100% exporters and zero-export firms excluded

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| CMIE Prowess (firm-level, 2008-2020) | Same source, extended to 2023 | CMIE ProwessIQ |
| RBI Handbook of Statistics on Indian States | Same source | RBI website (freely available) |
| DPIIT patent data | Same source | Annual Report, Office of Controller General of Patents |
| DPIIT Ease of Doing Business scores | Same or updated BRAP rankings | DPIIT/World Bank sub-national assessments |

#### 5.2 Suggested Variable Mapping
- EXPINT → Exports / Net sales (from Prowess)
- RDINT → R&D expenditure / Net sales
- CGIINT → Import of capital goods / Net sales
- RMINT → Imported raw materials / Net sales
- RPINT → Royalties and technical fees / Net sales
- INDRMINT → Indigenous raw materials / Net sales
- ADVINT → Advertisement + marketing + distribution expenses / Net sales
- OUTINT → Outsourcing payments / Net sales
- STINT → Staff welfare and training expenses / Net sales
- MNEs → Dummy: 1 if foreign equity > 10%
- AGE → Current year − year of incorporation
- SIZE → Log of gross fixed assets
- PATENT_rt → State-level patent applications filed (from Patent Office publications)
- KFIRMS_rt → Number of knowledge-intensive firms in state (from Prowess, mapped via Eurostat KIA classification)
- EASE_r → State's average ease of doing business score/rank (DPIIT)
- BANK_rt → Number of bank branches in state (RBI)

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Access CMIE ProwessIQ; filter by OECD high-tech and medium-high-tech manufacturing NIC codes; download RBI state-level statistics; obtain patent filing data from DPIIT annual reports.
2. **Data cleaning:** Drop firms never reporting sales; remove 100% exporters and perpetual non-exporters; retain firms appearing ≥3 times in panel; match state-level variables by firm registered state.
3. **Variable construction:** Compute all intensity ratios; classify industries by OECD technology intensity; map Eurostat knowledge-intensive activity (KIA) codes to NIC for KFIRMS variable; compute state-level patent counts.
4. **Econometric estimation:** Estimate QMLE model using `glm` with binomial family and logit link in Stata (or `fracreg logit`); include industry and year dummies; estimate Tobit model for comparison. Run disaggregated models for individual HT industries.
5. **Robustness checks:** Use two-part model (Probit for export participation + OLS/GLM for export intensity conditional on exporting); add lagged technological variables; use system GMM to address potential endogeneity of R&D; test with alternative technology classifications.

#### 5.4 Potential Challenges in Indian Replication
- CMIE Prowess subscription required
- Mapping OECD technology classification to Indian NIC codes requires careful concordance
- Eurostat KIA to NIC mapping for the knowledge-intensive firms variable is non-trivial
- State-level patent data may not be consistently available across all years
- Potential endogeneity of R&D and technology imports to export performance is not instrumented

### 6. Replication Difficulty Level
**Moderate** – Data is accessible (Prowess + publicly available state-level data), and the QMLE/Tobit methods are well-documented. The main challenges are in constructing location-specific variables and mapping technology classifications.

### 7. Recommended for Student Replication?
**Yes** – Well-structured study using Prowess data with clear variable definitions; the QMLE technique is a valuable learning exercise for handling fractional response variables; students can update to more recent data.

---

## Paper 34: Productivity Growth and Levels – A Comparison of Formal and Informal Manufacturing in India

### 1. Citation
* **Authors:** K. L. Krishna, Bishwanath Goldar, Suresh Chand Aggarwal, Deb Kusum Das, Abdul A. Erumban, and Pilu Chandra Das
* **Year:** 2018
* **Journal/Working Paper:** CDE Working Paper No. 291, Centre for Development Economics, Delhi School of Economics, University of Delhi
* **DOI/Link:** http://www.cdedse.org/pdf/work291.pdf

### 2. Abstract (Concise Summary)
This paper undertakes a comparative analysis of total factor productivity (TFP) growth and levels between formal (organised) and informal (unorganised) manufacturing sectors in India for the period 1980-81 to 2011-12, using the India KLEMS database (version 2016). TFP growth is measured via a gross output function framework using Tornqvist indices, with Domar aggregation for sector-level aggregates. The study finds that average TFP growth in informal manufacturing (0.6% per annum) was significantly lower than in formal manufacturing (4.4% per annum) over 1980–2011. Both segments experienced declining TFP growth during 1994–2002 followed by marked acceleration during 2003–2011. The acceleration in formal manufacturing TFP is driven mainly by coke and petroleum products, while in informal manufacturing it is attributable to textiles and leather. Comparison of TFP levels reveals substantially lower productivity in informal manufacturing. A more detailed 25-industry decomposition analysis for 2010-11 identifies the sources of the formal-informal TFP gap.

### 3. Data Used in the Original Study
| Component | Details |
|-----------|---------|
| Country/Region | India |
| Data Source | India KLEMS database (version 2016); underlying sources: National Accounts Statistics (NAS, 2004-05 series), Annual Survey of Industries (ASI), NSSO surveys on unorganised manufacturing and employment-unemployment, Input-Output Transaction Tables (IOTT) |
| Time Period | 1980-81 to 2011-12 (TFP growth); 2003-04 to 2011-12 (TFP level comparison); 2010-11 (detailed 25-industry analysis) |
| Unit of Analysis | Industry (13 major manufacturing industry groups; 25 industries for detailed analysis) |
| Sample Size | 13 industries × 32 years for TFP growth; 25 industries for level analysis |
| Key Variables | Gross output, gross value added (GVA), capital input (gross fixed capital stock), labour input (persons employed, UPSS basis), intermediate inputs (energy, materials, services), factor income shares, TFP growth (Tornqvist index), relative TFP levels (formal/informal) |

### 4. Econometric Methodology
- **Model type:** Growth accounting (not regression-based); Tornqvist index-based TFP measurement; Domar aggregation for sector-level TFP
- **Main estimating equations:**
  - TFP growth (gross output framework):
    ΔlnA_it = ΔlnY_it − s̄_K,it·ΔlnK_it − s̄_L,it·ΔlnL_it − s̄_E,it·ΔlnE_it − s̄_M,it·ΔlnM_it − s̄_S,it·ΔlnS_it
    where Y = gross output; K, L, E, M, S = capital, labour, energy, materials, services inputs; s̄ = two-period average income shares
  - Relative TFP (formal vs. informal):
    ln RTFP_j = s̄_K,j · ln RKP_j + s̄_L,j · ln RLP_j
    where RKP = relative capital productivity, RLP = relative labour productivity
  - Aggregate TFP via Domar aggregation using input-output-based Domar weights
- **Identification strategy:** Non-parametric growth accounting; no econometric estimation; TFP is the Solow residual under constant returns to scale and competitive factor markets
- **Key assumptions:** Constant returns to scale; competitive factor and product markets; translog production function (Tornqvist index is exact for translog); labour input measured by persons employed (no quality adjustment for formal-informal comparison due to data limitations)

### 5. Replication Feasibility in Indian Context

#### 5.1 Closest Indian Data Sources
| Original Data | Indian Substitute | Suggested Source |
|--------------|-------------------|-----------------|
| India KLEMS database (version 2016) | India KLEMS database (latest version, e.g., 2023 update) | RBI / India KLEMS project website (https://rbi.org.in) |
| ASI summary data | Same, extended to latest year | MoSPI ASI publications |
| NSSO unorganised manufacturing surveys | NSSO/PLFS surveys | MoSPI microdata portal |
| NAS 2004-05 series | NAS 2011-12 series | CSO/MoSPI National Accounts Statistics |
| Input-Output Transaction Tables | Latest IOTT (2017-18 or 2018-19 if available) | CSO |

#### 5.2 Suggested Variable Mapping
- Gross output → GVO from ASI (formal) and NSSO (informal), deflated using commodity-specific WPI
- GVA → From NAS, split into registered/unregistered using ASI and NSSO
- Capital stock → Perpetual inventory method using ASI (formal) and NSSO (informal) data
- Labour → Persons employed (UPSS) from NSSO EUS/PLFS, adjusted for population using Census
- Energy, Materials, Services inputs → Split intermediate inputs using IOTT benchmark ratios with linear interpolation
- Factor income shares → Labour share from wage bills (ASI for formal; NSSO establishments for informal); capital share as residual
- TFP → Tornqvist residual from KLEMS growth accounting

#### 5.3 Step-by-Step Replication Plan
1. **Data acquisition:** Access India KLEMS database (latest version from RBI website); obtain ASI summary results; access NSSO unorganised manufacturing survey data and Employment-Unemployment Survey / PLFS data; obtain Input-Output tables from CSO.
2. **Data cleaning:** Construct consistent 13-industry classification across NAS/ASI/NSSO using NIC concordance; ensure NAS 2004-05 series consistency (or shift to 2011-12 base); apply ASI corrections where relevant; split NAS aggregates into formal/informal using ASI and NSSO proportions.
3. **Variable construction:** Compute gross output, value added, capital stock, labour input, and intermediate input (E, M, S) series separately for formal and informal segments of each industry; compute factor income shares; construct Tornqvist indices.
4. **Econometric estimation:** Compute TFP growth rates for each industry and each segment; compute Domar-aggregated TFP for aggregate formal and informal manufacturing; compute relative TFP levels using Equation (7) for formal vs. informal comparison.
5. **Robustness checks:** Use value-added framework as alternative to gross-output framework; compare with KLEMS 2023 version estimates; extend period to 2017-18 or later using NSSO 2015-16 unorganised manufacturing data; decompose TFP differences by input contributions; test sensitivity to alternative capital stock measures.

#### 5.4 Potential Challenges in Indian Replication
- Constructing consistent time series across NAS base-year revisions (2004-05 vs. 2011-12 series) is technically challenging
- Post-2011-12, NAS does not separately report registered and unregistered manufacturing (reports corporate vs. household segment instead), making extension beyond 2011-12 difficult without imputation
- NSSO unorganised manufacturing surveys are conducted infrequently (quinquennial); inter-survey interpolation introduces approximation
- Labour quality adjustment is not feasible separately for formal and informal due to data limitations
- Domar aggregation requires detailed input-output tables, which are published with significant lags
- India KLEMS database may not be updated to the latest year

### 6. Replication Difficulty Level
**Hard** – The growth accounting methodology is conceptually straightforward but data construction is extremely demanding, requiring integration of multiple official statistical sources (NAS, ASI, NSSO, IOTT), careful concordance across classifications, and handling of base-year changes in national accounts.

### 7. Recommended for Student Replication?
**With caution** – Excellent for advanced students interested in productivity measurement and the formal-informal manufacturing divide, but the data construction demands are substantial; students should use the India KLEMS database directly rather than building series from scratch, and focus on updating TFP comparisons for a recent sub-period.

---

# Comparative Summary Table

| Paper No | Title | Method | Data Type | Indian Data Availability | Difficulty |
|----------|-------|--------|-----------|--------------------------|------------|
| 1 | FDI and R&D: Substitutes or Complements | Heckman two-step (HECKIT) | Firm-level panel | High | Moderate |
| 2 | Atmanirbhar Bharat Abhiyan | Panel GLS (Random Effects) | Industry-level panel | High | Moderate |
| 3 | Profitability in India's Organized Mfg. | Profit rate decomposition | Aggregate time series | High | Easy |
| 4 | Organised vs. Unorganised Mfg. Comparison | Descriptive ratio analysis | Cross-section (ASI + NSS) | High | Easy |
| 5 | ICT Adoption in Unorganized Firms | Ordinal Probit | Cross-section (ASUSE) | High | Easy to Moderate |
| 6 | Productivity–Investment Nexus, Informal | Log-linear OLS | Cross-section (ASUSE) | High | Easy |
| 7 | Firm Size & Productivity, Informal Sector | Pseudo-panel RE/Dynamic; Wooldridge-OP TFP | Pseudo-panel (NSS rounds) | High | Hard |
| 8 | FDI and Growth: Sector Effects | Cross-section OLS | Cross-country | Moderate | Moderate |
| 9 | Trade Liberalization & FDI in India | Panel FE/RE | Industry-level panel | High | Moderate |
| 10 | Diversification of Informal Mfg. Sector | Location quotients / Diversification coefficients | Cross-section (NSS) | High | Easy |
| 11 | Long-run Performance, Organised Mfg. | Bai-Perron breaks; Shift-share decomposition | Industry-level panel (ASI) | High | Moderate |
| 12 | Product Scope & Productivity (Dereservation) | DID with firm/year FE; Levinsohn-Petrin TFP | Firm-level panel (ASI) | High | Hard |
| 13 | Regional Concentration, Unorganised Mfg. | Concentration ratios / HHI | Cross-section (NSS) | High | Easy |
| 14 | Industrial Location & Spatial Inequality | Translog cost function (SUR); Logistic/OLS | Plant-level + district cross-section | High | Hard |
| 15 | Subcontracting & Informal Sector Size | Panel FE with interactions | State-industry panel (ASI + NSS) | High | Moderate |
| 16 | Indian Mfg.: Finance, Investment, Performance | Simultaneous dynamic panel GMM | Firm-level panel (Prowess) | Moderate | Moderate |
| 17 | Partial Privatization & Firm Performance | Firm FE; Arellano-Bond GMM | Firm-level panel (SOEs) | Moderate | Hard |
| 18 | FDI Impact on R&D (Medium/High-Tech) | Probit / Tobit | Firm-level cross-section | High | Moderate |
| 19 | Regional Mfg. Productivity (Org. & Unorg.) | ACF semi-parametric TFP | Plant-level panel (ASI + NSS/ASUSE) | High | Hard |
| 20 | Concentration & R&D Determinants | Arellano-Bond dynamic panel GMM | Industry-level panel (Prowess) | Moderate | Moderate |
| 21 | Subcontracting & Informal Sector Efficiency | Heckman selection; Oaxaca-Blinder decomposition | Cross-section (NSS) | High | Moderate |
| 22 | Foreign Investment & Firm Performance | DID with PSM | Firm-level panel | High | Moderate |
| 23 | Gender Productivity Gaps, Informal Mfg. | Descriptive / KS tests / kernel density | Cross-section (ASUSE) | High | Easy |
| 24 | Industry & the Urge to Cluster (Informal) | Count models (Poisson/NB); IV | District-industry cross-section | High | Hard |
| 25 | R&D Strategy of SMEs in India | Censored Quantile Regression (CQR) | Firm-level panel (Prowess) | Moderate | Moderate to Hard |
| 26 | Innovation & Employment, Indian Mfg. | Panel GLS | Firm-level panel (Prowess) | Moderate | Easy |
| 27 | Formal Subcontracting & Informal Employment | Panel FE with interactions | State-industry panel (ASI + NSS) | High | Moderate |
| 28 | Subcontracting & Efficiency (DEA) | Two-stage DEA + Tobit | Cross-section (NSS) | High | Moderate |
| 29 | R&D in Organised Mfg.: Tech-SMEs | Cragg double-hurdle; Heckman | Firm-level panel (ASI) | High | Moderate |
| 30 | R&D Determinants, Pharma (OFDI) | Probit / Tobit / Panel FE-RE | Firm-level panel (Prowess) | High | Easy to Moderate |
| 31 | International Trade & Productivity Growth | Panel RE/FE; FGLS | Industry-level panel (ASI) | High | Moderate |
| 32 | Determinants of Innovation (Survey-based) | Panel Probit | Firm-level panel (Primary survey + Prowess) | Low | Hard |
| 33 | Technological Capabilities & Exports | QMLE (fractional response); Tobit | Firm-level panel (Prowess) | High | Moderate |
| 34 | Productivity: Formal vs. Informal Mfg. | Growth accounting (Tornqvist/Domar) | Industry-level time series (KLEMS) | High | Hard |
