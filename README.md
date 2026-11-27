# Denmark Electricity Data (2026)

Open CSV datasets covering Danish 15-minute wholesale electricity prices in DK1 and DK2 (62,208 intervals from 1 January to 20 November 2026), residential C-tariffs across Denmark's 7 largest grid operators (DataHub Q4 2026), and annual home EV charging costs for 15,000 km/year.

All figures come from public Energinet Energi Data Service records (`DayAheadPrices` and `DatahubPricelist`) combined with the 2026 Danish electricity tax rate (0.8 øre/kWh ex. VAT, 1.0 øre incl. VAT) and 25% VAT. Live quarter-hour prices and calculators are published at [dagensel.dk](https://dagensel.dk/).

## Dansk opsummering

Dette repository samler tre åbne CSV-datasæt fra [DagensEl.dk](https://dagensel.dk/) baseret på 62.208 officielle 15-minutters spotpriser fra Energinet (1. januar til 20. november 2026) samt 2026 C-nettariffer fra DataHub for de 7 største danske netselskaber (Cerius, Radius, N1, Vores Elnet, Dinel, Konstant Net og TREFOR).

Hovedtal fra 2026:
- **Middag (kl. 12-15) slog nat (kl. 00-06) til elbilen:** På årsgennemsnittet kostede 15.000 km elbil (2.700 kWh) 2.561 til 3.258 kr. ved middagsladning mod 3.550 til 3.768 kr. ved natteladning og 5.359 til 7.064 kr. i kogespidsen kl. 17-21.
- **Storebælt deler de negative timer:** DK1 havde 203 negative timer (831 kvarterer) mod 94 negative timer (371 kvarterer) i DK2.
- **2,69 gange forskel i vinterens kogespids:** Cerius opkræver 129,75 øre/kWh inkl. moms kl. 17-21, mens TREFOR El-net opkræver 48,29 øre/kWh.

Brug de live værktøjer på [dagensel.dk](https://dagensel.dk/), [elpriser i morgen](https://dagensel.dk/elpriser-i-morgen/) (opdateres kl. 13:00), [elbil-opladning](https://dagensel.dk/elbil-opladning/), [apparatberegneren](https://dagensel.dk/stromforbrug/) (vaskemaskine, opvaskemaskine, tørretumbler, ovn og induktion) samt [varmepumpe-beregneren](https://dagensel.dk/varmepumpe-strom/).

---

## Datasets in this repository

| File | Coverage | Live report (Danish) |
|---|---|---|
| [`data/elbil-opladning-2026.csv`](data/elbil-opladning-2026.csv) | Annual home EV charging cost for 15,000 km (2,700 kWh) across 7 DSOs: night (00-06), midday (12-15), peak (17-21) | [Elbil-opladning 2026](https://dagensel.dk/rapporter/elbil-opladning-2026/) |
| [`data/elpriser-dk1-dk2-2026.csv`](data/elpriser-dk1-dk2-2026.csv) | Monthly DK1 and DK2 spot averages, negative hours, negative 15-min intervals, min/max prices (Jan to 20 Nov 2026) | [Negative elpriser 2026](https://dagensel.dk/rapporter/negative-elpriser/) |
| [`data/nettariffer-danmark-2026.csv`](data/nettariffer-danmark-2026.csv) | Winter and summer low/high/peak C-tariffs for 7 Danish DSOs plus per-40 kWh winter EV savings | [Kogespids og nettariffer 2026](https://dagensel.dk/rapporter/kogespids-nettariffer/) |

---

## 1. Home EV Charging Cost Across 7 Danish DSOs (2026)

Benchmark: 15,000 km/year at 18 kWh/100 km including charging losses (2,700 kWh/year, split 50% winter Oct-Mar and 50% summer Apr-Sep). Total prices include Energinet 2026 YTD average spot price in each time band, local DSO C-tariff, Energinet system/transmission tariffs (11.5 øre/kWh ex. VAT), 2026 electricity tax (0.8 øre/kWh ex. VAT), and 25% VAT.

Across all 7 grid operators, midday solar charging (12:00 to 15:00) finished cheaper on the 2026 annual average than overnight charging (00:00 to 06:00), despite higher daytime grid tariffs. In winter (October to February), overnight charging stays cheapest; from March to September, solar midday spot prices (0.539 kr/kWh DK1 and 0.583 kr/kWh DK2 ex. VAT vs. 0.886 and 0.878 kr/kWh overnight) pull the annual total down.

| DSO | Zone | Night 00-06 (kr/yr) | Midday 12-15 (kr/yr) | Peak 17-21 (kr/yr) | Saved: night vs. peak | Saved: midday vs. peak | kr/km (night / midday / peak) |
|---|---|---:|---:|---:|---:|---:|---:|
| Cerius A/S | DK2 | 3,768 | 3,258 | 7,064 | 3,296 | 3,806 | 0.25 / 0.22 / 0.47 |
| Radius Elnet A/S | DK2 | 3,737 | 3,188 | 6,865 | 3,128 | 3,677 | 0.25 / 0.21 / 0.46 |
| N1 A/S | DK1 | 3,702 | 2,902 | 6,337 | 2,635 | 3,435 | 0.25 / 0.19 / 0.42 |
| Vores Elnet A/S | DK1 | 3,643 | 2,786 | 6,013 | 2,370 | 3,227 | 0.24 / 0.19 / 0.40 |
| Dinel A/S | DK1 | 3,613 | 2,703 | 5,765 | 2,152 | 3,062 | 0.24 / 0.18 / 0.38 |
| Konstant Net A/S | DK1 | 3,610 | 2,695 | 5,743 | 2,133 | 3,048 | 0.24 / 0.18 / 0.38 |
| TREFOR El-net A/S | DK1 | 3,550 | 2,561 | 5,359 | 1,809 | 2,798 | 0.24 / 0.17 / 0.36 |

---

## 2. Energinet 2026 Spot Prices and Negative Hours (DK1 vs. DK2)

Period covered: 1 January to 20 November 2026 (324 full days, 31,104 quarter-hours per bidding zone, 62,208 total intervals).
- YTD average spot price (ex. VAT / incl. VAT): **0.8957 / 1.1196 kr/kWh** in DK1 and **0.9169 / 1.1461 kr/kWh** in DK2.
- Negative hours (hourly mean < 0 kr): **203 hours** (2.61% of all hours; 831 quarter-hours, 2.67%) in DK1 vs. **94 hours** (1.21%; 371 quarter-hours, 1.19%) in DK2.
- Cheapest average clock hour: **13:00 to 14:00** in both zones (0.4861 kr/kWh ex. VAT in DK1, 0.5294 kr/kWh in DK2).

| Month | DK1 avg incl. VAT (kr/kWh) | DK1 neg. hours | DK1 neg. quarters | DK2 avg incl. VAT (kr/kWh) | DK2 neg. hours | DK2 neg. quarters | DK2 minus DK1 ex. VAT (kr/kWh) |
|---|---:|---:|---:|---:|---:|---:|---:|
| 2026-01 | 0.9859 | 0 | 0 | 1.0261 | 0 | 0 | 0.0321 |
| 2026-02 | 0.8974 | 0 | 0 | 1.0592 | 0 | 0 | 0.1294 |
| 2026-03 | 0.9107 | 7 | 31 | 0.9061 | 5 | 21 | -0.0037 |
| 2026-04 | 0.7768 | 49 | 206 | 0.7413 | 29 | 125 | -0.0284 |
| 2026-05 | 0.9339 | 49 | 194 | 0.9302 | 34 | 136 | -0.0029 |
| 2026-06 | 1.0288 | 27 | 104 | 1.0180 | 10 | 35 | -0.0086 |
| 2026-07 | 0.9528 | 49 | 195 | 0.9590 | 10 | 32 | 0.0049 |
| 2026-08 | 1.1704 | 3 | 17 | 1.1859 | 2 | 7 | 0.0124 |
| 2026-09 | 1.3167 | 17 | 72 | 1.3392 | 4 | 15 | 0.0180 |
| 2026-10 | 1.4917 | 2 | 12 | 1.5211 | 0 | 0 | 0.0236 |
| 2026-11 (1-20) | 2.2065 | 0 | 0 | 2.3157 | 0 | 0 | 0.0873 |

---

## 3. Residential Grid Tariffs (DataHub Q4 2026, Tarifmodel 3.0)

Winter peak tariffs (17:00 to 21:00) vary by 2.69x between Denmark's priciest and cheapest major DSO: Cerius charges 129.75 øre/kWh incl. VAT versus 48.29 øre/kWh at TREFOR El-net (a 81.46 øre/kWh gap).

| DSO | Zone | Tariff code | Winter low (øre incl. VAT) | Winter high (øre incl. VAT) | Winter peak 17-21 (øre incl. VAT) | Summer peak (øre incl. VAT) | Winter peak minus low (øre) | Saved per 40 kWh charge (kr) |
|---|---|---|---:|---:|---:|---:|---:|---:|
| Cerius A/S | DK2 | `30TR_C_ET` | 14.42 | 43.25 | 129.75 | 56.23 | 115.34 | 46.13 |
| Radius Elnet A/S | DK2 | `DT_C_01` | 13.27 | 39.82 | 119.45 | 51.76 | 106.17 | 42.47 |
| N1 A/S | DK1 | `CD` | 10.98 | 32.95 | 98.84 | 42.83 | 87.85 | 35.14 |
| Vores Elnet A/S | DK1 | `TNT1011` | 9.61 | 28.84 | 86.53 | 31.09 | 76.91 | 30.77 |
| Dinel A/S | DK1 | `TCL<100_02` | 7.69 | 23.08 | 69.24 | 30.00 | 61.55 | 24.62 |
| Konstant Net A/S | DK1 | `C_FBTNTR_B` | 7.56 | 22.70 | 68.11 | 29.51 | 60.55 | 24.22 |
| TREFOR El-net A/S | DK1 | `C` | 5.36 | 16.10 | 48.29 | 20.93 | 42.93 | 17.17 |

---

## Column Dictionary

### `data/elbil-opladning-2026.csv`
- `netselskab`: Distribution system operator name.
- `omraade`: Bidding zone (`DK1` west of Great Belt, `DK2` east of Great Belt).
- `aarligt_forbrug_kwh`: Benchmark annual EV consumption (2,700 kWh = 15,000 km at 18 kWh/100 km).
- `nat_00_06_kr_pr_kwh_inkl_moms`: All-in average price per kWh during 00:00-06:00 incl. VAT (DKK).
- `middag_12_15_kr_pr_kwh_inkl_moms`: All-in average price per kWh during 12:00-15:00 incl. VAT (DKK).
- `kogespids_17_21_kr_pr_kwh_inkl_moms`: All-in average price per kWh during 17:00-21:00 incl. VAT (DKK).
- `nat_aar_15000km_dkk`: Annual home EV charging cost for 2,700 kWh at 00:00-06:00 (DKK).
- `middag_aar_15000km_dkk`: Annual home EV charging cost for 2,700 kWh at 12:00-15:00 (DKK).
- `kogespids_aar_15000km_dkk`: Annual home EV charging cost for 2,700 kWh at 17:00-21:00 (DKK).
- `besparelse_nat_vs_kogespids_dkk`: Annual DKK saved by charging at 00:00-06:00 instead of 17:00-21:00.
- `besparelse_middag_vs_kogespids_dkk`: Annual DKK saved by charging at 12:00-15:00 instead of 17:00-21:00.
- `kr_pr_km_nat`, `kr_pr_km_middag`, `kr_pr_km_kogespids`: All-in electricity cost per km in DKK incl. VAT.

### `data/elpriser-dk1-dk2-2026.csv`
- `maaned`: Calendar month (`YYYY-MM`; `2026-11` covers 1 to 20 November 2026).
- `dk1_gns_spot_ex_moms_kr_kwh`, `dk2_gns_spot_ex_moms_kr_kwh`: Unweighted monthly mean wholesale spot price ex. VAT (DKK/kWh).
- `dk1_gns_spot_inkl_moms_kr_kwh`, `dk2_gns_spot_inkl_moms_kr_kwh`: Monthly mean spot price incl. 25% VAT (DKK/kWh).
- `dk1_negative_timer`, `dk2_negative_timer`: Count of clock hours with an hourly average below 0 DKK/kWh.
- `dk1_negative_kvarterer`, `dk2_negative_kvarterer`: Count of 15-minute intervals below 0 DKK/kWh.
- `dk1_min_kr_kwh`, `dk1_max_kr_kwh`, `dk2_min_kr_kwh`, `dk2_max_kr_kwh`: Lowest and highest 15-minute spot price ex. VAT in that month (DKK/kWh).
- `forskel_dk2_minus_dk1_kr_kwh`: Monthly mean price spread DK2 minus DK1 ex. VAT (DKK/kWh).

### `data/nettariffer-danmark-2026.csv`
- `netselskab`, `omraade`, `tarifkode`: DSO name, bidding zone, and official DataHub C-tariff charge code.
- `vinter_lavlast_ex_moms_kr`, `vinter_hoejlast_ex_moms_kr`, `vinter_spidslast_ex_moms_kr`: Winter tariff bands ex. VAT (DKK/kWh).
- `vinter_lavlast_inkl_moms_oere`, `vinter_hoejlast_inkl_moms_oere`, `vinter_spidslast_inkl_moms_oere`: Winter tariff bands incl. 25% VAT (øre/kWh).
- `sommer_lavlast_inkl_moms_oere`, `sommer_hoejlast_inkl_moms_oere`, `sommer_spidslast_inkl_moms_oere`: Summer tariff bands incl. 25% VAT (øre/kWh).
- `vinter_spids_minus_lav_oere_inkl_moms`: Winter peak (17-21) minus winter low (00-06) spread incl. VAT (øre/kWh).
- `elbil_40kwh_vinter_besparelse_kr`: Grid-tariff savings on a single 40 kWh winter EV charge shifted from 17-21 to 00-06 (DKK incl. VAT).
- `kilde_periode`: Validity window reported in DataHub.

---

## Primary Official Sources and Live Tools

- Energi Data Service (Energinet): [DayAheadPrices](https://www.energidataservice.dk/tso-electricity/DayAheadPrices)
- Energi Data Service (Energinet): [DatahubPricelist](https://www.energidataservice.dk/tso-electricity/DatahubPricelist)
- Energinet: [Aktuelle tariffer 2026](https://energinet.dk/el/elmarkedet/tariffer/aktuelle-tariffer/)
- Skatteministeriet: [Elafgift 2026](https://skm.dk/)
- Energistyrelsen / SparEnergi: [Appliance kWh benchmarks](https://sparenergi.dk/)

Live tools on DagensEl.dk:
- Live 15-minute and hourly prices (DK1/DK2, cheapest 2/3/4h windows): https://dagensel.dk/
- Tomorrow's electricity prices hour by hour (updated daily ~13:00 CET): https://dagensel.dk/elpriser-i-morgen/
- Home EV charging window calculator: https://dagensel.dk/elbil-opladning/
- Household appliance cost calculator (washing machine, dishwasher, tumble dryer, oven, induction, heat pump): https://dagensel.dk/stromforbrug/
- Heat pump electricity cost calculator 2026/2027 (SCOP, air-to-water, ground-source, 7 DSOs): https://dagensel.dk/varmepumpe-strom/
- Reports index: https://dagensel.dk/rapporter/
- Lightweight iframe embeds (no sign-up): `https://dagensel.dk/embed/elpriser/` and `https://dagensel.dk/embed/elbil/`

## License and Citation

Licensed under [Creative Commons Attribution 4.0 International (CC-BY-4.0)](LICENSE). Please attribute **DagensEl.dk** (`https://dagensel.dk/rapporter/`). See [`CITATION.cff`](CITATION.cff) for machine-readable metadata.

```text
DagensEl.dk (2026). Denmark Electricity Data 2026: Energinet Spot Prices (DK1/DK2), 7-DSO Grid Tariffs, and Home EV Charging Costs [Dataset]. https://dagensel.dk/rapporter/ (CC-BY-4.0).
```
