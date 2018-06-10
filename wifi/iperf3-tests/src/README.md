# raspberry pi 3 B+ wifi benchmarking

I've ran a few tests with the Raspberry Pi 3 B+ working as an AP:

I've ran a series of `iperf3` tests, according to the following parameters:
* **Protocol:** UDP
* **Client(s):** Either (1) my Macbook Pro 2015, or (2) an eeePC laptop with a USB WiFi dongle based on the Ralink RT5572 chipset.
* **Server:** Raspberry Pi 3 B+, working as an AP, channel 36 (5.18 GHz) 40 MHz channel bandwidth
* **Target bitrates:** 11, 54, 72, 100, 120 and 150 Mbps
* **Duration of a single run:** 10 seconds
* **Nr. of runs per bitrate:** 5

## Results

It seems that the results are both influenced by the client and server side.

### Macbook Pro 2015 client

![macbook-results](https://www.dropbox.com/s/5h48p7148dbvfr8/rpi-wifi.macbook.png?dl=1)

* The measured bitrate (line and dots in red above) closely follows the target bitrate
* Packet losses larger thann 10% start occurring at 120 Mbps
* The CPU usage at the Raspberry Pi side stays below 10%

### Ralink 5572 USB dongle client

![ralink-results](https://www.dropbox.com/s/e9x2qf31fdku780/rpi-wifi.ralink.png?dl=1)

* The measured bitrate stays below the target bitrate, starting from 72 Mbps. In fact, I can never get higher than 90 Mbps.
* Packet loss is relatively low (below 1%). I've checked that wireless link retries were on, up to a max. limit of 1 retry (I couldn't configure the USB dongle to 0 retries).
* CPU utilization at the Raspberry Pi side is still below 10%.
