# Errata: original CIS 540 report (Dec 2022)

1. **API credentials are visible in the report.** A screenshot shows the Twitter consumer key and secret plus the access token and secret. Revoke them in the developer portal, and never publish the original PDF. The corrected write-up contains no screenshots of code with secrets.

2. **The malicious-link rate is inconsistent.** The results say an average of 1–2 malicious URLs per day out of about 300 (roughly 0.3–0.7%), but the conclusion says "approximately 1%". The corrected write-up uses the per-day figures.

3. **"Malicious" was never defined.** The report doesn't say how many VirusTotal engines had to flag a URL. This is now stated as a limitation.

4. **Automation was overstated.** The abstract describes "an automated program, like an API", but the method says the scripts were run manually every day. The write-up now calls it semi-automated.

5. **The VirusTotal description is out of date.** "More than 40 antivirus products" is replaced with a general description, because VirusTotal now aggregates around 70 engines.

6. **There was no control group**, so the claim that attackers exploit trending topics is supported by prior work, not by this data. Now disclosed as a limitation.

7. **Chart labels have typos.** "TwitterBinge" should read "Twitter→Bing", and the axis titles say "FIELD1".

8. **The conclusion contradicts itself.** It says conclusions are "very difficult" and then claims a "conclusive analysis". This is removed.

9. **Reproducibility.** Twitter's free API access ended in 2023, and the Bing Search APIs were retired in 2025. Both are noted in the README.
