# Scanner
An attempt to automate reconnaissance and integrate it in pipeline.

0. Distributed Scanning:
   - Axiom Scan

1. Subdomain Enumeration:   
   - amass enum -brute -active -d domain.com -o amass-output.txt
   - subfinder -d example.com -o example_subdomains.txt
   - cat amass-output.txt | dnsgen -

2. Filter Out Duplicates:   
   - cat new-output.txt | anew old-output.txt

3. Active Hosts:   
   - cat example_subdomains.txt | httpx -o live_web_hosts.txt
   - cat amass-output.txt | httprobe -p http:81 -p http:3000 -p https:3000 -p http:3001 -p https:3001 -p http:8000 -p http:8080 -p https:8443 -c 50 | tee online-domains.txt

4. Images of the domains:
   - cat live_web_hosts.txt | aquatone

5. Port Scanning:
   - nmap -iL live_web_hosts.txt -p- --min-rate 1000 -oN nmap_full_scan.txt
  
6. Tech Detection:
   - cat live_web_hosts.txt | httpx -tech-detect -o tech_fingerprint.txt
  
7. Directory Busting:
   - ffuf -ac -v -u https://domain/FUZZ -w wordlist.txt
   - gau example.com --subs --o gau_root_and_subs_urls.txt
  
8. Parameter Fuzzing:
   - arjun -u https://target.example.com/api/users

9. Javascript endpoints analysis:
    - Linkfinder and secretfinder

10. Subdomain Takeover:
    - subzy run --targets list_of_subs.txt
