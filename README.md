
# Cybersecurity Lab: Week 2, PM1 to PM5

**Name:** Muhammad Hassan Tariq
**Batch:** B084

# PM1: Footprinting & Reconnaissance with Multiple Kali Tools

## Objective
Build a profile of the course-provided target `networkwalks.com` using six built-in Kali Linux tools: whois, whatweb, nslookup, curl, wafw00f and dnsrecon.

## Steps

### Step 1: Run whois
Opened a terminal in Kali Linux and queried the domain registration record (registrar, creation/expiry dates, name servers).

```bash
whois networkwalks.com
```

![whois output]<img width="720" height="686" alt="whois" src="https://github.com/user-attachments/assets/6b5dbb12-2703-439a-87ee-41d1fee2ec06" />


### Step 2: Run whatweb
Fingerprinted the web technologies (web server, CMS, plugins, IP address).

```bash
whatweb networkwalks.com
```

<img width="1256" height="238" alt="whatweb" src="https://github.com/user-attachments/assets/e0156024-3783-49b6-99b7-bb11414652da" />


### Step 3: Run nslookup
Resolved the domain name to its IP address.

```bash
nslookup networkwalks.com
```

![nslookup output]<img width="712" height="412" alt="nslookup" src="https://github.com/user-attachments/assets/608440eb-c8ef-4892-9a85-69f1c24daabd" />


### Step 4: Run curl
Read the HTTP response headers (status, server banner, cookies, redirects).

```bash
curl -I https://networkwalks.com
```

![curl headers](<img width="1263" height="445" alt="curl" src="https://github.com/user-attachments/assets/c4e4d73e-27e3-45ac-8ecb-11de3105a28e" />
)

### Step 5: Run wafw00f
Checked whether a Web Application Firewall is protecting the site.

```bash
wafw00f networkwalks.com
```

![wafw00f output](<img width="712" height="412" alt="nslookup" src="https://github.com/user-attachments/assets/73a7545c-51cd-40ab-abee-2f3c710a919f" />
)


### Step 6: Run dnsrecon
Enumerated DNS records (name servers, mail servers, SPF/TXT and SRV records).

```bash
dnsrecon -d networkwalks.com
```

![dnsrecon output](<img width="1122" height="412" alt="dnsrecon" src="https://github.com/user-attachments/assets/c55fd137-52bc-42ae-bd5c-c40ef89d2d88" />
)

### Step 7: Save the outputs
Saved a screenshot of every command and copied each output into a text file for the final report.

## Notes
No major issues encountered. dnsrecon showed a "No answer for DNSSEC query" message, which is expected when DNSSEC is not enabled on the domain.

---

# PM2: Footprinting & Reconnaissance with GHDB

## Objective
Use Google dorks from the Exploit-DB Google Hacking Database (GHDB) to find publicly indexed information through Google alone: exposed camera interfaces (Task 1) and open directories containing mathematics PDF ebooks (Task 2).

## Steps

### Step 1: Open GHDB
Opened [exploit-db.com](https://www.exploit-db.com) and clicked **GHDB** in the left-side menu.

![Exploit-DB GHDB](<img width="1327" height="917" alt="image" src="https://github.com/user-attachments/assets/af284023-4f6f-4ef9-8405-bbd12e34aab0" />
)

### Step 2: Search for dorks
Searched the term `cam` in GHDB and copied dorks one by one.

![GHDB dork list](<img width="1662" height="762" alt="image" src="https://github.com/user-attachments/assets/6e30fabe-aee3-4a34-8753-0946384d2314" />
)

### Step 3: Run the dorks on Google (Task 1)
Pasted each dork into Google and opened the results to check them, for example:

```
intitle:"webcamXP" inurl:8080
intitle:"Live View / - AXIS"
inurl:/view/index.shtml
```

![Dork search on Google](<img width="1012" height="772" alt="image" src="https://github.com/user-attachments/assets/17ac547c-2137-4647-b9ee-facebc947689" />
)

### Step 4: Find mathematics PDF listings (Task 2)
Searched this dork on Google and opened each listing to confirm it contained downloadable PDFs:

```
intitle:index.of "parent directory" mathematics pdf
```

![Math PDF directory listing](<img width="681" height="750" alt="image" src="https://github.com/user-attachments/assets/e7a73094-657a-42b1-b214-c96021232789" />
)

### Step 5: Record the findings
Recorded each link, its dork and any credentials in the tables of the lab document.

## Notes
The exact camera links and IP addresses are not published in this repository because they belong to real people and organizations. Only the dork patterns are documented. Some results were dead links or required a login, so several dorks had to be tried.

---

# PM3: Footprinting with Maltego

## Objective
Install Maltego on a Windows computer (Task 1) and find the email addresses related to `networkwalks.com` with permission (Task 2).

## Steps

### Step 1: Download Maltego
Downloaded Maltego Graph for Windows from maltego.com.

![Maltego download](<img width="1202" height="880" alt="image" src="https://github.com/user-attachments/assets/320e9395-6eab-4c62-b091-950f1ae07f83" />
)

### Step 2: Install Maltego
Ran the setup file as administrator. The installer also installed the required Java runtime (JRE 17).

![Maltego installation](<img width="635" height="517" alt="Screenshot 2026-11-10 115934" src="https://github.com/user-attachments/assets/78002e16-01ee-4227-bae5-07b5a1923ecd" />
)

### Step 3: Activate with a Maltego ID
Launched Maltego, selected **Maltego ID** with online activation, accepted the license and clicked **Browser Login**. Created a free Maltego ID in the browser and returned to Maltego with the default settings (default system browser, Privacy Mode: Normal).

![Maltego activation](<img width="758" height="662" alt="Screenshot 2026-11-10 120631" src="https://github.com/user-attachments/assets/ed09000a-5575-48a5-86a6-fe16543ed221" />
)

### Step 4: Add the domain entity
Searched for **Domain** in the Entity Palette, dragged it onto the graph and renamed it to `networkwalks.com`.

![Domain entity](<img width="1722" height="922" alt="Screenshot 2026-11-10 122832" src="https://github.com/user-attachments/assets/d3cda901-40b5-4345-8e60-69b1c1b93220" />
)

### Step 5: Run email transforms
Right-clicked the entity, filtered for email-related transforms and ran them.

![Email transforms](<img width="1727" height="917" alt="Screenshot 2026-11-10 123838" src="https://github.com/user-attachments/assets/34a5cc69-75f4-4683-aeb9-1b7f397b24c3" />
)

### Step 6: Review the results
The email addresses related to the domain were harvested and shown on the graph.

![Email results](<img width="1732" height="920" alt="Screenshot 2026-11-10 125535" src="https://github.com/user-attachments/assets/1473ddc6-7625-4879-9384-0fdc96be4dc6" />
)

## Notes
If Maltego does not redirect automatically after the browser login, click Back in the setup wizard and log in again. The Community Edition uses credits for transforms and limits the number of results.

---

# PM4: Footprinting & Reconnaissance with theHarvester

## Objective
Gather email IDs and sub-domains related to `microsoft.com` (public information only) using theHarvester in Kali Linux, first with the Baidu source (limit 1000) and then with all sources (limit 50).

## Steps

### Step 1: Open theHarvester and read the usage guide
Opened a terminal in Kali Linux and checked the available options and supported sources.

### Step 2: Search with Baidu (Task 1)
Ran theHarvester with Baidu as the source and a limit of 1000 results. `-d` is the target domain, `-l` limits the results and `-b` sets the data source.

```bash
theHarvester -d microsoft.com -l 1000 -b baidu
```

![Baidu search](<img width="671" height="690" alt="Screenshot 2026-11-08 085721" src="https://github.com/user-attachments/assets/9052e855-f2fc-4de1-afca-2f70e692e1ef" />
)

### Step 3: Search with all sources (Task 2)
Ran theHarvester with all sources and a limit of 50 results.

```bash
theHarvester -d microsoft.com -l 50 -b all
```

![All sources search](<img width="685" height="542" alt="Screenshot 2026-11-11 142244" src="https://github.com/user-attachments/assets/ea802dd1-ac23-448c-9000-733482595d37" />
)

### Step 4: Save the outputs
Saved the screenshots and copied the outputs into text files.

## Notes
With `-b all`, many sources printed "Missing API key" errors and were skipped because no API keys were configured. Results differ from the lab guide because the public sources keep changing, but the method stays the same.

---

# PM5: Network Scanning with Zenmap

## Objective
Install Zenmap, find my local IP address and LAN subnet, discover the live hosts with a ping scan, identify their IP and MAC addresses, and save the network topology as a PDF.

## Steps

### Step 1: Find the local IP and subnet
Opened Command Prompt and ran `ipconfig` to find the PC's IP address and subnet mask.

```cmd
ipconfig
```

![ipconfig output](<img width="618" height="262" alt="Screenshot 2026-11-11 142744" src="https://github.com/user-attachments/assets/c7191521-6499-4483-b421-d3a810447bf7" />
)

### Step 3: Run a ping scan
Opened Zenmap, entered the LAN subnet as the target, selected the **Ping scan** profile and clicked **Scan** (equivalent to `nmap -sn <subnet>`).

![Ping scan results](<img width="1066" height="782" alt="Screenshot 2026-11-08 075841" src="https://github.com/user-attachments/assets/b44a50bd-2694-49e6-ada9-5c6ca1708ee2" />
)

### Step 4: Record the live hosts
Counted the live hosts and noted their IP and MAC addresses. Used `ipconfig /all` to find the local PC's MAC address.

| Question | Answer |
|----------|--------|
| Live hosts | _3_ |
| IP addresses | _10.0.0.1,10.0.0.2,10.0.0.3_ |
| MAC addresses | _52:54:00:12:35:00,08:00:27:C5:39:CE_ |

### Step 5: Save the topology as PDF
Opened the **Topology** tab, turned on the legend, clicked **Save Graphic** and selected **PDF**. The file was saved on the desktop.

## Notes
Ping scans only find hosts that answer ping, so devices that block ICMP may not appear. The subnet and results depend on the local network, so they differ from the lab guide's 10.0.0.0/24 example.
