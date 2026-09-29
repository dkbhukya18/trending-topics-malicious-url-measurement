# Measuring Malicious Links in Trending-Topic Search Results

Course project for CIS 540, University of Michigan-Dearborn, Fall 2022.
Team: Ashish Vardhan Avuluri, Dileep Kumar Bhukya, Prakruthi Hosakere Srinivas, Sai Yeswanth Maturi, Vinutha Gowdru Parameshwarappa.

This is a **corrected** write-up of the original report. [ERRATA.md](ERRATA.md) lists every change.

## Question

Attackers use SEO poisoning to piggyback on trending topics: they push malicious pages into search results for whatever people are currently searching. How often do top search results for trending topics point to URLs that security vendors flag?

## Method

1. **Collect trending topics each day** from Google trends, Bing, and Twitter/X trending hashtags. Twitter hashtags were turned into links by running them through Google search.
2. **Collect the top search result URLs** for each topic through the Google and Bing search APIs, about 300 URLs per day.
3. **Scan each URL with the VirusTotal API.** VirusTotal reports how many engines rate a URL harmless, undetected, suspicious or malicious.
4. **Repeat daily for about 30 days** (Nov–Dec 2022), for roughly 9,000 URLs in total. The collection scripts were started manually each day.

## Results

- Flagged URLs were rare: on average 1–2 per day as malicious and a similar number as suspicious, out of about 300 scanned. **That is roughly 0.3–0.7% per day.** The peak day had 9 malicious URLs (about 3%).
- The original data doesn't record how many engines flagged each URL, so single-engine flags (often false positives) can't be separated from multi-engine consensus.

## Limitations

- **No detection threshold was defined.** Standard practice is to require two or more engines, or a vendor reputation score, before calling a URL malicious.
- **URLs weren't de-duplicated across days**, so the same popular URL may be counted many times.
- **There was no baseline.** The project didn't compare trending-topic results against random or non-trending queries, so it can't show that trending topics are *more* dangerous.
- **VirusTotal verdicts at scan time are a snapshot.** Many malicious URLs are flagged only days later, and the scans were not repeated.
- **The pipeline can't be reproduced as built.** Twitter's free API access ended in 2023, and Microsoft retired the Bing Search APIs in 2025. A re-implementation would need current alternatives.

## Next steps

Automate collection on a schedule instead of running it by hand. Rescan flagged and a sample of clean URLs after 7 days, and add a non-trending control group. For deeper analysis of flagged URLs, use a sandbox or detailed-report service such as urlscan.io.

## References

1. T. Wu et al. *Analysis of Trending Topics and Text-based Channels of Information Delivery in Cybersecurity.* ACM TOIT 22(2), 2022.
2. S. Abu et al. *Cyber Threat Intelligence – Issues and Challenges.* Indonesian J. Electrical Eng. & CS 10(1), 2018.
3. N. Bar-Yosef. *How Attackers Use Search Engines and How You Can Fight Back.* SecurityWeek, 2011.
4. VirusTotal API v3 documentation: https://docs.virustotal.com/reference/overview
