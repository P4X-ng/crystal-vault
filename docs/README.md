# Crystal Vault

<p align="center">
  <img src="Wanted%20Poster.PNG" alt="Wanted Poster" width="600">
</p>

![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2FRingmast4r%2Fcrystal-vault&label=Visitors&countColor=%23CF142B)
![GitHub repo size](https://img.shields.io/github/repo-size/Ringmast4r/crystal-vault?color=%23FFCC00&label=Repo%20Size)
![GitHub stars](https://img.shields.io/github/stars/Ringmast4r/crystal-vault?style=flat&color=%23FFCC00)
![GitHub forks](https://img.shields.io/github/forks/Ringmast4r/crystal-vault?style=flat&color=%2300247D)
![GitHub last commit](https://img.shields.io/github/last-commit/Ringmast4r/crystal-vault?color=%23CF142B)
![GitHub issues](https://img.shields.io/github/issues/Ringmast4r/crystal-vault?color=%23FFCC00)
![License](https://img.shields.io/badge/License-Public%20Domain-green)

**Documenting Venezuela's surveillance infrastructure through their own open APIs.**

> *The regime built a vault. They forgot to lock it.*

## [**LIVE DASHBOARD**](https://ringmast4r.github.io/crystal-vault/) | [**GLOSSARY**](https://ringmast4r.github.io/crystal-vault/glossary.html) | [**TIMELINE**](https://ringmast4r.github.io/crystal-vault/timeline.html)

---

## What Is Crystal Vault?

On December 24-26, 2025, Venezuela's SAIME (identity agency) announced migration to **"La Bóveda de Cristal"** (The Crystal Vault) — a centralized database merging citizen identity records, banking data, and social program participation for 30+ million Venezuelans.

Built by **ZTE Corporation (China)**, this system consolidates:
- SAIME (national ID / cedulas)
- BCV (central banking)
- Sistema Patria (social programs / surveillance)
- CNE (voter registration) — suspected

This repository documents what I found when I looked at their public infrastructure.

---

## The Irony

They built a surveillance system to track every citizen.

They announced it on a **WordPress blog with open REST APIs**.

I pulled their entire office network, operational statistics, and infrastructure documentation — **no authentication required**.

---

## What's In This Repository

### Exfiltrated Data (`/exfil`) - 4.34 GB Total
| Source | Files | With EXIF | GPS Coords | Description |
|--------|-------|-----------|------------|-------------|
| INCES | 3,167 | 571 | **16** | National training institute - largest collection |
| AVN | 2,813 | 704 | **2** | State news agency |
| Correo | 1,438 | 950 | 0 | State newspaper |
| SAREN | 1,117 | 364 | 0 | Registry and notary service |
| VTV | 457 | 193 | 0 | State television |
| CANTV | 421 | 113 | 0 | State telecommunications |
| SAIME | 298 | 5 | 0 | Identity agency + 134 office GPS |
| Patria | 5 | 1 | 0 | Social programs platform |

**Total: 9,716 media files | 2,901 with EXIF | 18 staff phone GPS locations**

### EXIF Intelligence (`/exfil/reports`)
| File | Description |
|------|-------------|
| `EXIF_REPORT_FULL.json` | Complete metadata dump for all 2,901 files |
| `STAFF_PHONE_GPS_INTEL.json` | 18 government staff phone GPS locations |
| `ALL_GPS_COORDINATES.json` | All 152 GPS coordinates (134 offices + 18 phones) |

### OFAC Sanctions Cross-Reference
| File | Size | Description |
|------|------|-------------|
| `OFAC_Sanctions/venezuela_sanctions.csv` | 112KB | 470 Venezuela-related sanctioned entities |
| `OFAC_Sanctions/venezuela_parsed.json` | 152KB | Parsed with extracted cedula numbers |

### Interactive Dashboard
| File | Description |
|------|-------------|
| `index.html` | Map with layer toggles, EXIF intel, GPS tracking, sanctions search |
| `glossary.html` | 80+ Venezuelan terms translated for Americans |
| `timeline.html` | Venezuela events July 2024 - December 2025 |

---

## Key Findings

### Operational Statistics (from their own posts)
- **7,257** cedulas issued to fishermen (tracking fishing communities)
- **15,511** indigenous IDs issued (tracking native populations)
- **56,785** workers ID'd at workplaces (employment surveillance)
- **127,415** processed at Plaza Caracas in 2025
- **21.8 million** Sistema Patria users (as of Jan 2023)

### Sanctioned Individuals with Cedulas
I extracted ~210 cedula numbers from OFAC sanctions data:

| Name | Cedula | Role |
|------|--------|------|
| Tareck El Aissami | 12.354.211 | Former VP, drug trafficking |
| Hugo Carvajal Barrios | 8.352.301 | Former intel chief |
| Gustavo González López | 5.726.284 | SEBIN director |
| Henry Rangel Silva | 5.764.952 | Defense minister |
| Freddy Bernal Rosales | 5.665.018 | Táchira governor |

### Infrastructure Exposed
```
https://www.saime.gob.ve/wp-json/

OPEN ENDPOINTS (no auth):
  /wp/v2/posts     → News with operational data
  /wp/v2/pages     → Service documentation
  /wp/v2/media     → Government images
  /geodir/v2/places → 100 office GPS coordinates
```

---

## For Researchers

This data enables:
- **Mapping government capacity** — 134 office locations visualized
- **Sanctions enforcement** — Cedula cross-referencing
- **Infrastructure analysis** — Understanding regime digital systems
- **Humanitarian planning** — Office accessibility for displaced persons

## For Journalists

Key angles:
- Chinese tech (ZTE) building Venezuelan surveillance
- Christmas 2025 database merger announcement
- Open APIs exposing what should be secured
- 7+ million refugees whose data remains in the system

## For the 7+ Million Venezuelan Refugees

Your data is still in Crystal Vault. The regime can:
- Track family members who remain
- Monitor financial activity through BCV integration
- Cross-reference voting patterns with benefits

This documentation exists so you know what they have.

---

## Legal & Ethical Notes

**All data collected from:**
- Publicly accessible REST APIs (no authentication bypassed)
- US Government public records (OFAC Treasury)
- Standard open-source intelligence methods

**No private systems were accessed.** This is what anyone with a browser and `curl` can retrieve. That's the point — the regime that surveils everyone forgot to secure anything.

---

## How to Use the Dashboard

1. Open `index.html` in any browser (or visit the [live dashboard](https://ringmast4r.github.io/crystal-vault/))
2. Tabs: Overview | Office Map | OFAC Sanctions | Operations | API | Media
3. Search sanctions by name or cedula number
4. Click map markers for office details

---

## Data Sources

| Source | URL | Type |
|--------|-----|------|
| SAIME WordPress API | `saime.gob.ve/wp-json/` | Government |
| OFAC SDN List | `treasury.gov/ofac/downloads/` | US Government |
| Sistema Patria | `patria.org.ve` | Documented |
| cedula.com.ve API | `api.cedula.com.ve` | Third-party (paid) |

---

## Contributing

If you have:
- VPN access to geoblocked .gob.ve sites
- Additional OSINT on Venezuelan infrastructure
- Translations or context

Open an issue or PR.

---

## Validation Reports

Independent validation of repository claims:

- **[Validation Summary](VALIDATION_SUMMARY.md)** — Quick reference with claim verification status
- **[Validation Report](VALIDATION_REPORT.md)** — Comprehensive analysis with evidence assessment
- **[Information Tree](INFORMATION_TREE.md)** — Claim-by-claim evidence mapping

These reports provide independent verification of data sources, file counts, and claims made in this repository.

---

## Related

- [OFAC Venezuela Sanctions](https://www.treasury.gov/resource-center/sanctions/Programs/pages/venezuela.aspx)
- [Vendata.org](https://vendata.org) — Venezuelan open data
- [HDX Venezuela Data](https://data.humdata.org/dataset/cod-ps-ven) — Humanitarian datasets

---

<p align="center">
  <i>"La Bóveda de Cristal"</i><br>
  <b>A vault made of glass.</b>
</p>
