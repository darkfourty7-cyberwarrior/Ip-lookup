🔴 DARK IP CONNECTOR

IP Intelligence & Approximate Geolocation Tool for Termux

DARK IP CONNECTOR is a lightweight Python-based IP intelligence and network information tool designed for Termux on Android.

The project provides a simple terminal interface for looking up IP addresses and displaying information that is publicly available through an IP intelligence service. It is designed with a dark/red Matrix-style interface and focuses on network information, ISP identification, ASN information, timezone data, and approximate geolocation.

«Made by DARK 47»

---

📸 Screenshot

"DARK IP CONNECTOR" (Screenshot_20260912_093247_Termux.jpg)

---

✨ Features

DARK IP CONNECTOR includes several useful features for IP intelligence and network research.

🔎 IP Lookup

Enter an IPv4 or IPv6 address and retrieve available information about the network.

The tool can display:

- IP address
- IP version
- Continent
- Country
- Country code
- Region
- City
- Postal code
- Approximate latitude
- Approximate longitude
- Timezone
- ISP
- Organization
- ASN
- Domain

🌐 Public IP Detection

The tool can automatically detect the public IP address of the network currently being used by the device.

This can be useful when you want to quickly determine which public IP is visible to an external service.

📍 Approximate Geolocation

The tool can display approximate geographic information associated with an IP address.

Depending on the available database information, this may include:

- Country
- Region
- City
- Postal code
- Latitude
- Longitude
- Timezone

Geolocation should always be treated as an estimate rather than an exact physical location.

🏢 ISP & Organization Information

DARK IP CONNECTOR can identify available network ownership information such as:

- Internet Service Provider
- Organization
- Autonomous System Number
- Domain

This can help identify whether an address belongs to an ISP, hosting provider, CDN, cloud provider, or other network.

📜 Lookup History

Previous lookups can be stored locally so that you can review them later.

🗑️ Clear History

The stored lookup history can be cleared from the tool.

---

📦 Installation

DARK IP CONNECTOR is designed to run directly inside Termux.

1. Install Termux

Install Termux from a trusted source and open the application.

Make sure your device has an active internet connection.

2. Update Termux

Run:

pkg update -y
pkg upgrade -y

3. Install Python

pkg install python -y

4. Install Requests

DARK IP CONNECTOR uses the Python "requests" library for HTTP requests.

pip install requests

5. Clone the Repository

Clone the official GitHub repository:

git clone https://github.com/darkfourty7-cyberwarrior/Ip-lookup.git

6. Enter the Directory

cd Ip-lookup

7. Run DARK IP CONNECTOR

python dark_ip.py

---

🚀 Quick Installation

If Python is already installed, the basic installation can be completed with:

pkg update -y
pkg install python -y
pip install requests
git clone https://github.com/darkfourty7-cyberwarrior/Ip-lookup.git
cd Ip-lookup
python dark_ip.py

---

🖥️ Menu

When the program starts, you will see the DARK IP CONNECTOR interface.

The menu provides options similar to:

1. Scan / Lookup IP
2. Detect My Public IP
3. Lookup History
4. Clear History
5. About DARK IP CONNECTOR
0. Exit

Select an option by entering its corresponding number.

---

🔍 IP Lookup Example

Select:

1

The program will ask for an IP address.

For example:

8.8.8.8

The tool then requests publicly available IP intelligence information and displays the returned results.

A result may look similar to:

[+] IP ADDRESS        : 8.8.8.8
[+] IP VERSION        : IPv4
[+] CONTINENT         : North America
[+] COUNTRY           : United States
[+] COUNTRY CODE      : US
[+] REGION            : California
[+] CITY              : ...
[+] LATITUDE          : ...
[+] LONGITUDE         : ...
[+] TIMEZONE          : ...
[+] ISP               : ...
[+] ORGANIZATION      : ...
[+] ASN               : ...
[+] DOMAIN            : ...

The exact information depends on the IP intelligence provider and its available database.

---

🌐 Public IP Detection

To detect the public IP of your current connection, select:

2

The program obtains the public-facing IP address and can then use that address for an IP information lookup.

Keep in mind that your public IP may belong to your ISP, mobile carrier, VPN, proxy, corporate network, or another network provider.

---

📊 Information Explained

IP Address

The numerical address being investigated.

IP Version

Identifies whether the address is IPv4 or IPv6.

Country

The country associated with the IP according to the geolocation database.

Region

The approximate administrative region associated with the address.

City

An approximate city-level geolocation result.

Latitude / Longitude

Approximate coordinates associated with the IP database entry.

ISP

The Internet Service Provider or network operator associated with the address.

Organization

The organization associated with the network.

ASN

The Autonomous System Number associated with the network.

Domain

A domain associated with the organization or network when available.

Timezone

The timezone associated with the approximate geographic result.

---

⚠️ Important Geolocation Disclaimer

IP geolocation is not GPS tracking.

An IP address generally cannot be used by this tool to determine the exact physical location of a person.

For example, an IP address may belong to:

- An Internet Service Provider
- A mobile carrier
- A VPN
- A proxy
- A CDN
- A cloud provider
- A hosting company
- A corporate network
- Shared infrastructure
- A network gateway

As a result, the displayed city and coordinates may represent a network or infrastructure location rather than the physical location of the person using the connection.

Therefore, results should be treated as approximate intelligence, not proof of someone's exact location or identity.

---

🔐 Privacy & Security

DARK IP CONNECTOR is intended for legitimate network-information purposes.

Do not use this project to harass, stalk, threaten, impersonate, or target individuals.

Only investigate IP addresses when you have a legitimate reason and are permitted to do so.

The project does not claim to provide exact-person tracking.

---


📁 Project Structure

A typical project directory contains:

Ip-lookup/
│
├── dark_ip.py
├── README.md
├── Screenshot_20260912_093247_Termux.jpg
└── dark_ip_history.json

The history file may be created automatically after performing lookups.

---

🛠️ Troubleshooting

Python command not found

Install Python:

pkg install python -y

Requests module missing

Run:

pip install requests

Repository directory not found

Check your current directory:

pwd

Then list the files:

ls

Enter the repository:

cd Ip-lookup

Check Python syntax

Before running the program, you can check the script with:

python -m py_compile dark_ip.py

If there is no output, the syntax check completed successfully.

---

🔄 Update the Tool

To update your local copy from GitHub:

cd Ip-lookup
git pull

Then run:

python dark_ip.py

---

🌟 GitHub

Official repository:

DARK IP CONNECTOR — Ip-lookup

https://github.com/darkfourty7-cyberwarrior/Ip-lookup

If you find the project useful, consider giving the repository a ⭐ star.

---

👤 Author

DARK 47

DARK IP CONNECTOR was created as a Termux-based IP intelligence project for learning about networks, IP addressing, ASN information, ISP infrastructure, and approximate IP geolocation.

«Made by DARK 47»

---

📜 Disclaimer

This software is provided for educational, research, and authorized security purposes.

The author is not responsible for misuse of this project.

Always follow applicable laws, regulations, terms of service, and authorization requirements when investigating network information.

IP intelligence databases can contain inaccurate, outdated, or incomplete information. Geographic results are estimates and should not be interpreted as exact physical locations.

Use responsibly. Stay legal. Learn. Build.
