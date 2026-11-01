## Abstract

Farm produce theft, livestock rustling, and rural banditry are a persistent problem for Nigerian agriculture, and conventional sensor-based security only makes it worse: PIR alarms fire on wind and stray animals until farmers stop trusting them, and intruders have adapted by wearing masks or balaclavas specifically to defeat CCTV identification.

In this project, an Intelligent Farm Intrusion Detection System (FAIDS) that pairs low-power IoT hardware at the edge with cloud-based inference to get around both problems at once was built. A Raspberry Pi 3B, wired to dual HC-SR501 PIR sensors and dual USB cameras and run off a 3S Li-ion pack with a BMS and buck converter, handles motion sensing and image capture. When something moves, the image is transmitted over an asynchronous FastAPI backend to a Microsoft Azure Custom Vision model trained to classify faces as either masked or unmasked, keeping the heavy inference off a device with no GPU to spare. A GPIO-triggered LED indicator gives an immediate local signal independent of the cloud round trip, while a React/Tailwind frontend dashboard and email pipeline handle the actual alerting.

In field testing, the power system ran on battery for over 15 hours to simulate grid outage, the PIR sensors caught human targets up to a distance of 5–6 m, and the vision model hit 99.6% mAP, with precision and recall both above 97%. Average end-to-end latency, from motion to alert in the farmer's email inbox, came out to 860 ms despite the flakiness of rural cellular coverage.

The results back up the core idea: cheap local sensors triggering enterprise-grade cloud inference is a workable, affordable way to secure off-grid farmland that neither pure edge nor pure cloud architectures handle well on their own.
