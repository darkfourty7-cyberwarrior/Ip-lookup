#!/usr/bin/env python3

import os
import sys
import time
import json
import random
import shutil
import requests
from datetime import datetime


# ============================================================
# DARK IP CONNECTOR
# Made by DARK 47
# Legitimate IP information / geolocation lookup
# ============================================================

APP_NAME = "DARK IP CONNECTOR"
VERSION = "1.0"
HISTORY_FILE = "dark_ip_history.json"

API_URL = "https://ipwho.is/"
REQUEST_TIMEOUT = 15


# ============================================================
# COLORS
# ============================================================

class C:
    BLACK = "\033[0;30m"
    RED = "\033[0;31m"
    GREEN = "\033[0;32m"
    YELLOW = "\033[0;33m"
    BLUE = "\033[0;34m"
    PURPLE = "\033[0;35m"
    CYAN = "\033[0;36m"
    WHITE = "\033[0;37m"

    BRIGHT_RED = "\033[1;31m"
    BRIGHT_GREEN = "\033[1;32m"
    BRIGHT_YELLOW = "\033[1;33m"
    BRIGHT_BLUE = "\033[1;34m"
    BRIGHT_PURPLE = "\033[1;35m"
    BRIGHT_CYAN = "\033[1;36m"
    BRIGHT_WHITE = "\033[1;37m"

    RESET = "\033[0m"
    BOLD = "\033[1m"


# ============================================================
# SCREEN
# ============================================================

def clear_screen():
    os.system("clear")


def terminal_size():
    try:
        size = shutil.get_terminal_size((80, 24))
        return size.columns, size.lines
    except Exception:
        return 80, 24


# ============================================================
# RED MATRIX RAIN
# ============================================================

def matrix_rain(duration=3.0):
    width, height = terminal_size()

    chars = (
        "0123456789"
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        "@#$%&*+-=[]{}<>"
    )

    drops = [
        random.randint(-height, 0)
        for _ in range(width)
    ]

    start = time.time()

    sys.stdout.write("\033[2J")
    sys.stdout.write("\033[H")
    sys.stdout.flush()

    try:
        while time.time() - start < duration:

            width, height = terminal_size()

            if len(drops) != width:
                drops = [
                    random.randint(-height, 0)
                    for _ in range(width)
                ]

            for x in range(width):

                y = drops[x]

                if 0 <= y < height:

                    char = random.choice(chars)

                    sys.stdout.write(
                        "\033["
                        + str(y + 1)
                        + ";"
                        + str(x + 1)
                        + "H"
                        + C.BRIGHT_RED
                        + char
                        + C.RESET
                    )

                drops[x] += 1

                if drops[x] > height + random.randint(0, 8):
                    drops[x] = random.randint(-height, 0)

            sys.stdout.flush()
            time.sleep(0.025)

    except KeyboardInterrupt:
        pass

    sys.stdout.write(C.RESET)
    sys.stdout.write("\033[2J")
    sys.stdout.write("\033[H")
    sys.stdout.flush()


# ============================================================
# BANNER
# ============================================================

def banner():

    print(
        C.BRIGHT_RED
        + r"""
██████╗  █████╗ ██████╗ ██╗  ██╗
██╔══██╗██╔══██╗██╔══██╗██║ ██╔╝
██║  ██║███████║██████╔╝█████╔╝
██║  ██║██╔══██║██╔══██╗██╔═██╗
██████╔╝██║  ██║██║  ██║██║  ██╗
╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝

██╗██████╗      ██████╗ ██████╗ ███╗   ██╗
██║██╔══██╗    ██╔════╝██╔═══██╗████╗  ██║
██║██████╔╝    ██║     ██║   ██║██╔██╗ ██║
██║██╔═══╝     ██║     ██║   ██║██║╚██╗██║
██║██║         ╚██████╗╚██████╔╝██║ ╚████║
╚═╝╚═╝          ╚═════╝ ╚═════╝ ╚═╝  ╚═══╝
"""
        + C.RESET
    )

    print(
        C.BRIGHT_CYAN
        + "             DARK IP CONNECTOR"
        + C.RESET
    )

    print(
        C.BRIGHT_YELLOW
        + "          IP INTELLIGENCE CONSOLE"
        + C.RESET
    )

    print(
        C.RED
        + "             Made by DARK 47"
        + C.RESET
    )

    print()


# ============================================================
# STARTUP
# ============================================================

def startup():

    clear_screen()

    matrix_rain(3)

    clear_screen()

    banner()

    print(
        C.BRIGHT_GREEN
        + "[ SYSTEM ONLINE ]"
        + C.RESET
    )

    time.sleep(0.4)

    print(
        C.GREEN
        + "[✓] Network module loaded"
        + C.RESET
    )

    time.sleep(0.3)

    print(
        C.GREEN
        + "[✓] IP intelligence module loaded"
        + C.RESET
    )

    time.sleep(0.3)

    print(
        C.GREEN
        + "[✓] Geolocation module ready"
        + C.RESET
    )

    time.sleep(0.5)

    print()


# ============================================================
# INPUT
# ============================================================

def pause():

    input(
        "\n"
        + C.BRIGHT_CYAN
        + "Press Enter to continue..."
        + C.RESET
    )


def is_valid_ip(ip):

    import ipaddress

    try:
        ipaddress.ip_address(ip)
        return True
    except ValueError:
        return False


# ============================================================
# HISTORY
# ============================================================

def load_history():

    if not os.path.exists(HISTORY_FILE):
        return []

    try:

        with open(
            HISTORY_FILE,
            "r",
            encoding="utf-8"
        ) as f:

            data = json.load(f)

        if isinstance(data, list):
            return data

    except Exception:
        pass

    return []


def save_history(data):

    try:

        with open(
            HISTORY_FILE,
            "w",
            encoding="utf-8"
        ) as f:

            json.dump(
                data[-50:],
                f,
                indent=2,
                ensure_ascii=False
            )

    except Exception:
        pass


def add_history(info):

    history = load_history()

    history.append(
        {
            "time": datetime.now().isoformat(
                timespec="seconds"
            ),
            "ip": info.get("ip", ""),
            "country": info.get("country", ""),
            "city": info.get("city", "")
        }
    )

    save_history(history)


# ============================================================
# API LOOKUP
# ============================================================

def lookup_ip(ip):

    try:

        print(
            "\n"
            + C.BRIGHT_YELLOW
            + "[*] Connecting to IP intelligence service..."
            + C.RESET
        )

        url = API_URL + ip

        response = requests.get(
            url,
            timeout=REQUEST_TIMEOUT
        )

        response.raise_for_status()

        data = response.json()

        if not data.get("success", False):

            error = data.get(
                "message",
                "Lookup failed."
            )

            print(
                C.RED
                + "[!] "
                + str(error)
                + C.RESET
            )

            return None

        return data

    except requests.exceptions.Timeout:

        print(
            C.RED
            + "[!] Request timed out."
            + C.RESET
        )

    except requests.exceptions.ConnectionError:

        print(
            C.RED
            + "[!] Could not connect to lookup service."
            + C.RESET
        )

    except requests.exceptions.HTTPError as e:

        print(
            C.RED
            + "[!] HTTP error: "
            + str(e)
            + C.RESET
        )

    except ValueError:

        print(
            C.RED
            + "[!] Server returned invalid JSON."
            + C.RESET
        )

    except Exception as e:

        print(
            C.RED
            + "[!] Lookup error: "
            + str(e)
            + C.RESET
        )

    return None


# ============================================================
# DISPLAY RESULT
# ============================================================

def show_result(data):

    clear_screen()
    banner()

    print(
        C.BRIGHT_CYAN
        + "════════════════════════════════════════"
        + C.RESET
    )

    print(
        C.BRIGHT_GREEN
        + "             IP INTELLIGENCE"
        + C.RESET
    )

    print(
        C.BRIGHT_CYAN
        + "════════════════════════════════════════"
        + C.RESET
    )

    ip = data.get("ip", "N/A")
    type_ = data.get("type", "N/A")

    continent = data.get("continent", "N/A")
    country = data.get("country", "N/A")
    country_code = data.get("country_code", "N/A")
    region = data.get("region", "N/A")
    city = data.get("city", "N/A")
    postal = data.get("postal", "N/A")
    latitude = data.get("latitude", "N/A")
    longitude = data.get("longitude", "N/A")
    timezone = data.get("timezone", "N/A")

    connection = data.get(
        "connection",
        {}
    )

    isp = connection.get(
        "isp",
        "N/A"
    )

    org = connection.get(
        "org",
        "N/A"
    )

    asn = connection.get(
        "asn",
        "N/A"
    )

    domain = connection.get(
        "domain",
        "N/A"
    )

    rows = [
        ("IP ADDRESS", ip),
        ("IP VERSION", type_),
        ("CONTINENT", continent),
        ("COUNTRY", country),
        ("COUNTRY CODE", country_code),
        ("REGION", region),
        ("CITY", city),
        ("POSTAL CODE", postal),
        ("LATITUDE", latitude),
        ("LONGITUDE", longitude),
        ("TIMEZONE", timezone),
        ("ISP", isp),
        ("ORGANIZATION", org),
        ("ASN", asn),
        ("DOMAIN", domain)
    ]

    print()

    for label, value in rows:

        print(
            C.BRIGHT_RED
            + "[+] "
            + label.ljust(18)
            + C.RESET
            + ": "
            + C.WHITE
            + str(value)
            + C.RESET
        )

    print()

    print(
        C.YELLOW
        + "NOTE: IP geolocation is approximate and"
        + C.RESET
    )

    print(
        C.YELLOW
        + "does not identify an exact person or address."
        + C.RESET
    )

    add_history(data)

    pause()


# ============================================================
# IP SCANNER
# ============================================================

def scan_ip():

    clear_screen()
    banner()

    print(
        C.BRIGHT_CYAN
        + "[ IP LOOKUP ]"
        + C.RESET
    )

    print(
        C.YELLOW
        + "Enter an IPv4 or IPv6 address."
        + C.RESET
    )

    print(
        C.YELLOW
        + "Example: 8.8.8.8"
        + C.RESET
    )

    ip = input(
        "\n"
        + C.BRIGHT_RED
        + "DARK-IP> "
        + C.RESET
    ).strip()

    if not ip:

        print(
            C.RED
            + "No IP address entered."
            + C.RESET
        )

        time.sleep(1)
        return

    if not is_valid_ip(ip):

        print(
            C.RED
            + "[!] Invalid IP address."
            + C.RESET
        )

        time.sleep(1.5)
        return

    data = lookup_ip(ip)

    if data:
        show_result(data)
    else:
        pause()


# ============================================================
# PUBLIC IP
# ============================================================

def public_ip():

    clear_screen()
    banner()

    print(
        C.BRIGHT_CYAN
        + "[ PUBLIC IP ]"
        + C.RESET
    )

    print(
        C.YELLOW
        + "Detecting your public IP..."
        + C.RESET
    )

    try:

        response = requests.get(
            "https://api.ipify.org?format=json",
            timeout=REQUEST_TIMEOUT
        )

        response.raise_for_status()

        data = response.json()

        ip = data.get("ip")

        if not ip:
            raise ValueError("No IP returned.")

        print()

        print(
            C.BRIGHT_GREEN
            + "Your public IP: "
            + C.BRIGHT_WHITE
            + ip
            + C.RESET
        )

        choice = input(
            "\n"
            + C.YELLOW
            + "Look up this IP? [Y/n]: "
            + C.RESET
        ).strip().lower()

        if choice in ("", "y", "yes"):

            result = lookup_ip(ip)

            if result:
                show_result(result)

    except Exception as e:

        print(
            C.RED
            + "[!] Could not detect public IP: "
            + str(e)
            + C.RESET
        )

        pause()


# ============================================================
# HISTORY VIEWER
# ============================================================

def show_history():

    clear_screen()
    banner()

    print(
        C.BRIGHT_CYAN
        + "[ LOOKUP HISTORY ]"
        + C.RESET
    )

    history = load_history()

    if not history:

        print(
            "\n"
            + C.YELLOW
            + "No lookup history."
            + C.RESET
        )

        pause()
        return

    print()

    for number, item in enumerate(
        reversed(history[-20:]),
        1
    ):

        print(
            C.BRIGHT_RED
            + str(number).rjust(2)
            + ". "
            + C.RESET
            + C.BRIGHT_WHITE
            + str(item.get("ip", "N/A"))
            + C.RESET
            + " | "
            + str(item.get("city", "N/A"))
            + ", "
            + str(item.get("country", "N/A"))
            + " | "
            + str(item.get("time", ""))
        )

    pause()


# ============================================================
# CLEAR HISTORY
# ============================================================

def clear_history():

    clear_screen()
    banner()

    print(
        C.BRIGHT_CYAN
        + "[ CLEAR HISTORY ]"
        + C.RESET
    )

    choice = input(
        "\n"
        + C.YELLOW
        + "Delete saved lookup history? [y/N]: "
        + C.RESET
    ).strip().lower()

    if choice in ("y", "yes"):

        try:

            if os.path.exists(HISTORY_FILE):
                os.remove(HISTORY_FILE)

            print(
                C.BRIGHT_GREEN
                + "\n[✓] History cleared."
                + C.RESET
            )

        except Exception as e:

            print(
                C.RED
                + "\n[!] Failed: "
                + str(e)
                + C.RESET
            )

    else:

        print(
            C.YELLOW
            + "\nCancelled."
            + C.RESET
        )

    time.sleep(1)


# ============================================================
# ABOUT
# ============================================================

def about():

    clear_screen()
    banner()

    print(
        C.BRIGHT_CYAN
        + "[ ABOUT ]"
        + C.RESET
    )

    print()

    print(
        C.WHITE
        + "DARK IP CONNECTOR "
        + VERSION
        + C.RESET
    )

    print(
        C.WHITE
        + "IP intelligence and approximate geolocation"
        + C.RESET
    )

    print(
        C.WHITE
        + "IPv4 / IPv6 lookup support"
        + C.RESET
    )

    print(
        C.WHITE
        + "ISP / ASN / organization information"
        + C.RESET
    )

    print(
        C.WHITE
        + "Local lookup history"
        + C.RESET
    )

    print()

    print(
        C.YELLOW
        + "Made by DARK 47"
        + C.RESET
    )

    print()

    print(
        C.BRIGHT_RED
        + "For authorized and legitimate network research."
        + C.RESET
    )

    pause()


# ============================================================
# MAIN MENU
# ============================================================

def main_menu():

    while True:

        clear_screen()
        banner()

        print(
            C.BRIGHT_CYAN
            + "════════════════════════════════════════"
            + C.RESET
        )

        print(
            C.BRIGHT_WHITE
            + "                 MENU"
            + C.RESET
        )

        print(
            C.BRIGHT_CYAN
            + "════════════════════════════════════════"
            + C.RESET
        )

        print(
            C.BRIGHT_RED
            + "1."
            + C.RESET
            + " Scan / Lookup IP"
        )

        print(
            C.BRIGHT_RED
            + "2."
            + C.RESET
            + " Detect My Public IP"
        )

        print(
            C.BRIGHT_RED
            + "3."
            + C.RESET
            + " Lookup History"
        )

        print(
            C.BRIGHT_RED
            + "4."
            + C.RESET
            + " Clear History"
        )

        print(
            C.BRIGHT_RED
            + "5."
            + C.RESET
            + " About DARK IP CONNECTOR"
        )

        print(
            C.BRIGHT_RED
            + "0."
            + C.RESET
            + " Exit"
        )

        print(
            C.BRIGHT_CYAN
            + "════════════════════════════════════════"
            + C.RESET
        )

        try:

            choice = input(
                "\n"
                + C.BRIGHT_RED
                + "IPconnector@Dark47> "
                + C.RESET
            ).strip()

            if choice == "1":

                scan_ip()

            elif choice == "2":

                public_ip()

            elif choice == "3":

                show_history()

            elif choice == "4":

                clear_history()

            elif choice == "5":

                about()

            elif choice == "0":

                print(
                    "\n"
                    + C.BRIGHT_RED
                    + "DARK IP CONNECTOR shutting down..."
                    + C.RESET
                )

                time.sleep(0.8)
                clear_screen()
                return

            else:

                print(
                    C.RED
                    + "\n[!] Invalid option."
                    + C.RESET
                )

                time.sleep(1)

        except KeyboardInterrupt:

            print(
                "\n"
                + C.RED
                + "Interrupted."
                + C.RESET
            )

            return


# ============================================================
# ENTRY POINT
# ============================================================

def main():

    try:
        import requests
    except ImportError:

        print("Installing requests...")

        os.system(
            "python -m pip install requests"
        )

        import requests

    startup()
    main_menu()


if __name__ == "__main__":
    main()
