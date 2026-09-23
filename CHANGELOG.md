# Changelog

All notable changes to EngineCreep are documented in this file.

The format is based on Keep a Changelog and follows Semantic Versioning.

---

## [2.0.0] - 2026-09-23

A ground-up rebuild. Every score now comes from a new evidence pipeline and is checked by a person before it is published. The catalogue restarts with 22 hand-reviewed BMW engines instead of 241 generated profiles, and the whole site is now also available in German.

### Added

- New evidence pipeline. Each engine is researched in one specific car, because the same engine code behaves differently in different cars. Owner reports are collected, filtered, grouped into 30 known failure types and confirmed before anything reaches a report.
- Human review of every engine before publication: the evidence behind each decision, the evidence that was left out and why, and whether the verdict and grade fit the rules.
- New data sources, strongest evidence first:
  - Official recalls from NHTSA (US) and the RDW (Netherlands).
  - NHTSA owner complaints.
  - Dated owner histories, such as Bring a Trailer listings.
  - Owner forums, including Bimmerpost, E90Post, BimmerForums, Motor-Talk and German and Russian BMW boards.
  - Reddit car and brand communities.
- Engine specs such as displacement, fuel type and production years, taken from Wikipedia and manufacturer data and checked against each other.
- Relevance filtering by a language model running on our own server, which reads every quote to check that it is about the part it mentions.
- Engine attribution rules that drop quotes about a different engine, which are common in comparison threads.
- Confidence scoring for every issue. Only confirmed issues appear on a report or count towards its score. Several posts in one thread count as one platform, so a single viral thread cannot manufacture a consensus.
- Wear or design flaw classification with six types, from expected maintenance to manufacturing defect, so normal wear does not count like a factory fault.
- Severity and frequency ratings for every confirmed issue.
- New grading method: an evidence score, plus two independent reputation checks from language models by two different companies, calibrated against 23 reference engines with well-established real-world records. No model is ever told where the score bands fall, and the buy recommendation is decided by code.
- Redesigned engine reports with five sections: Verdict, Specs, Known issues, Buying checklist and Sources.
- Typical repair price range for every failure type.
- A "When problems show up" chart with the mileage at which each confirmed issue typically starts appearing.
- Per-platform source breakdown on every report.
- German version of the site at `/de/`, including the verdicts and buying advice for all 22 engines. Guides stay in English.
- Curated lists: Most Reliable Diesel Engines, Most Reliable Petrol Engines, Cheapest Engines to Maintain, Old But Gold, and Best Engines for High Mileage.
- Methodology page explaining the sources, the confirmation rules and the grading in full.
- Contact form, and a "Something wrong here?" report form on every engine page.
- New buying guide: How to Check a Used Car Engine Before You Buy.
- Engine illustrations for each engine family.
- Share images for every engine, guide and the home page, in English and German.
- Social profiles in the footer: Instagram, X, TikTok and GitHub.

### Changed

- The catalogue now covers 22 BMW engines (B38, B47, B48, B57, B58, M20, M47, M50, M54, M57, M62, N13, N20 and N46), each in a specific car. More engines will be added as they pass the same review.
- All scores were recalculated from scratch with the new method. They currently range from 33 to 92 and are not comparable with 1.x scores.
- 1,419 sources now sit behind 168 confirmed issues across the catalogue.
- Engine verdicts, buying advice and owner summaries were edited by hand.
- The website was rebuilt from scratch with a new design. Listing pages load only lightweight data, and full reports are prerendered.
- The blog is now "Buying guides".
- A new not-found page for addresses that do not exist.

### Removed

- 223 of the 241 engine profiles from 1.1.0, which have not yet been through the new pipeline and review. Their pages now return "not found". The other 18 keep their address and were rebuilt from scratch.
- 25 older blog articles.
- Per-engine FAQ sections, maintenance schedules, ownership cost estimates and tuning risk assessments, which were not backed by evidence to the new standard.
- Amazon parts links, and the country detection behind them.

### Security

- Upgraded Next.js to 16.2.12, which fixes published vulnerabilities affecting form handling.
- Stricter Content Security Policy.
- Both forms have a bot trap and a rate limit, and form input cannot alter email headers.
- Structured data on every page is escaped.

### Infrastructure

- Engine data moved to Cloudflare D1, one record per engine, with lightweight columns for listing pages.
- Pages are served from Cloudflare Workers, with an hourly-refreshed page cache in Cloudflare R2.
- Share images are cached after they are first drawn.
- Every report records the scoring version that produced it.
- A maintenance page kept the site offline while the new version was deployed.

---

## [1.1.2] - 2026-08-01

### Fixed

- Fixed an issue affecting Cloudflare R2 integration that could prevent engine data from loading correctly.
- Improved R2 request handling and stability.
- Resolved edge cases related to remote asset retrieval.

---

## [1.1.1] - 2026-07-31

### Improved

- Migrated engine assets and static resources to Cloudflare R2.
- Significantly improved page loading speed.
- Reduced asset delivery latency.
- Optimized image delivery and caching performance.
- Improved overall user experience across the website.

---

## [1.1.0] - 2026-07-30

### Added

- Public launch of EngineCreep.
- Added **241 engine profiles** covering major manufacturers.
- Introduced comprehensive engine reliability scoring.
- Added common engine failure database.
- Added maintenance schedules.
- Added estimated repair costs.
- Added ownership cost estimates.
- Added recall information where available.
- Added tuning risk assessments.
- Added technical engine specifications.
- Added frequently asked questions for every engine.
- Added buying advice and ownership recommendations.
- Added manufacturer pages.
- Added engine comparison functionality.
- Added structured data for improved search engine visibility.
- Added Open Graph and social sharing support.
- Added responsive design for desktop and mobile devices.

### Infrastructure

- Built with Next.js.
- Static page generation for optimal performance.
- Search engine optimized architecture.
- Fast global content delivery.

---

## [1.0.0] - 2026-07-15

### Initial Development

- Started the EngineCreep project.
- Designed the database architecture.
- Built the first engine data models.
- Developed the first version of the website.
