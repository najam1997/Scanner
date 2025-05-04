# Scanner
An attempt to automate reconnaissance and integrate it in pipeline.

1. Subdomain Enumeration:   
   - amass enum -brute -active -d domain.com -o amass-output.txt
   - subfinder -d example.com -o example_subdomains.txt
   - cat amass-output.txt | dnsgen - | httprobe

2. Filter Out Duplicates:   
   - cat new-output.txt | anew old-output.txt

3. Active Hosts:   
   - cat example_subdomains.txt | httpx -o live_web_hosts.txt
   - cat amass-output.txt | httprobe -p http:81 -p http:3000 -p https:3000 -p http:3001 -p https:3001 -p http:8000 -p http:8080 -p https:8443 -c 50 | tee online-domains.txt

4. Images of the domains:
   - cat live_web_hosts.txt | aquatone

5. 
