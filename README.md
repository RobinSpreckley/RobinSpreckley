<div align="center">

# Robin Spreckley

**Software Engineer · Embedded Linux · Applied AI**

First Class MSci Computing Science, University of Glasgow  
Currently building software for a palm-vein biometric scanner at **Boop**, Edinburgh

<a href="https://www.linkedin.com/in/robin-s-657a5a20b/"><img src="https://img.shields.io/badge/LinkedIn-0f766e?style=for-the-badge&logo=linkedin&logoColor=white"></a>
<a href="mailto:robin.spreckley12@gmail.com"><img src="https://img.shields.io/badge/Email-0f766e?style=for-the-badge&logo=gmail&logoColor=white"></a>
<!-- Uncomment once the portfolio is deployed:
<a href="https://robinspreckley.vercel.app"><img src="https://img.shields.io/badge/Portfolio-0f766e?style=for-the-badge&logo=vercel&logoColor=white"></a>
-->

</div>

## ✦ about

```text
ROLE       Software engineer, open to junior and graduate roles

NOW        Boop: embedded Linux scanner software in C++, Rust and Python
           device provisioning, Bluetooth Wi-Fi setup, network telemetry

STACK      Python · Rust · C++ · TypeScript · SQL
           Linux · Docker · Git · CI/CD · Yocto · OpenTelemetry
           PyTorch · ONNX · TF-Lite · React · React Native

INTERESTS  Edge AI, explainable AI, making slow systems fast,
           tooling with Claude Code
```

## ✦ work at Boop

<sub>Palm-vein biometric scanner · Edinburgh · code is private, so these are summaries</sub>

### Network telemetry
`RUST` `OPENTELEMETRY` `GRAFANA`

Added per-device Wi-Fi signal, latency and failure-rate metrics so slow scanners can be diagnosed remotely. This exposed a bug where fast-failing connections were reported as online, hiding 61% of network failures in testing.

### One-command provisioning
`YOCTO` `LINUX` `TAILSCALE`

Turns a blank SD card into a remotely accessible scanner on Wi-Fi and Tailscale, with keys pre-signed for Tailnet Lock.

### Over-the-air updates restored
`RAUC` `YOCTO` `BASH` `PKI`

Got over-the-air updates working again. Built tools to sign update bundles and move existing scanners to a new signing key without reflashing. Tested end to end on hardware: wrongly signed updates are refused, and signed updates install to the A/B slots and boot cleanly.

### Phone setup over Bluetooth
`RUST` `REACT NATIVE` `BLE`

Extended the scanner agent and app so factory-fresh scanners can be connected and claimed from a phone.

### Faster startup
`C++` `RUST` `PYTHON`

Built a startup profiler for the scanner and optimised its initialisation.

### Deep Tech London showcase
`RUST` `LINUX` `TAILSCALE` `HARDWARE`

Built the kiosk provisioning for the team's live demo. One flash command clones a master SD card into a kiosk that boots with its own name, machine ID, SSH keys and Tailscale node, and opens the demo page chosen at flash time. Four kiosks were set up this way for the event, where the team's demo collected visitors' palm scans, generated investor interest and tested the full stack live.

<br>

## ✦ project archive

### Are LLM explanations faithful?
`PYTHON` `PYTORCH` `EXPLAINABLE AI` `LLMS`

Ongoing. Tests whether an LLM's explanation of its answer reflects what actually drove it. The model names the words behind its sentiment label; deleting them should hurt its answer far more than deleting random words.
- **First result (Qwen3-4B, 872 SST-2 reviews):** deleting the named words cut the model's confidence about 2.4× more than random words on average, but in 60% of reviews they did no better than random, and it named 69 words that weren't in the review.
- **Next:** log-odds and occlusion baselines, then judging response quality against human ratings (HelpSteer2), then agent decisions.

<a href="https://github.com/RobinSpreckley/llm-faithfulness"><img src="https://img.shields.io/badge/CODE-0f766e?style=for-the-badge&logo=github&logoColor=white"></a>

### Towards On-Orbit ML in Pico-Satellites
`PYTHON` `EDGE AI` `HARDWARE ACCELERATION` `PYTORCH`

MSci dissertation, industry task for Alba Orbital. **Top mark in the year.**
Built a benchmark showing which ML models and hardware fit on a picosatellite, because published work rarely reported real power, memory or runtime.
- **Models:** trained YOLOv5 and YOLOv8 object detectors in PyTorch on DIOR (23,463 satellite images), then converted them to TF-Lite with FP16 and INT8 quantisation and compiled them for the Coral Edge TPU.
- **Hardware:** set up six test configurations across a Raspberry Pi 3B+ with Coral TPU, an Odroid XU4 and an Odroid N2+ with Mali GPU (ArmNN), working through OS, driver and runtime version conflicts.
- **Measurement:** logged power at 10+ samples a second on an external machine, triggered over TCP so logging added no load to the board. Also recorded memory across all child processes and the time for each pipeline stage, and defined per-watt efficiency metrics for inference and the full pipeline.
- **Results:** YOLOv5n-FP16 on the N2+ GPU reached 0.897 mAP50 at 2.4 W peak power and 349 MB peak memory. YOLOv8 outputs a third as many boxes, so it was fastest end to end despite slower inference. With the model running entirely on the TPU, inference was about 2.4× more power-efficient than the GPU, but the Pi's CPU then became the bottleneck.

<a href="https://github.com/RobinSpreckley/TowardsOnObrbitMachineLearningInPicoSatellites"><img src="https://img.shields.io/badge/CODE-0f766e?style=for-the-badge&logo=github&logoColor=white"></a>

### Spying on Cows
`PYTHON` `ML` `EXPLAINABLE AI` `MYSQL`

BSc dissertation with Langhill Herd. **Top mark in the year.**
Built an ML pipeline to detect lameness from real farm sensor data.
- **Data:** cleaned six years of farm records (water troughs, milking, milk composition, weight, body condition, lactation, pedigree) and loaded them into a MySQL schema with Java uploaders, removing typos, conflicting date formats, duplicates and impossible values such as negative water intake.
- **Feature engineering:** built 100+ features over 24,500 rows. For each lameness score, aggregated every sensor stream over the 7 days before it (count, mean, std, min, max, sum) without using later readings. Treated zeros case by case: a milking that never happened was left out, but a visit to the water trough with no drinking was kept. Added days into lactation, age and season.
- **Models:** a neural network for every cow and one for the whole herd, on the same train/test split, with SMOTE-NC oversampling, grid search and cross-validation. The herd model scored best overall (F1 0.57, accuracy 0.74) but dropped the most when judged cow by cow, and oversampling improved the per-cow models.
- **Explainable AI:** ran LIME on every model, summarised as feature-importance charts and word clouds. This caught models relying on meaningless signals (the calendar year, the day of the week, who did the scoring) and showed the per-cow models used how consistent a cow's milking times were, a pattern the herd model missed.

<a href="https://github.com/RobinSpreckley/Spying-On-Cows"><img src="https://img.shields.io/badge/CODE-0f766e?style=for-the-badge&logo=github&logoColor=white"></a>

### Twitter Web Crawler
`PYTHON` `MONGODB` `SQL`

Python crawler with the Twitter API, using MongoDB and SQL for trend analysis.

<a href="https://github.com/RobinSpreckley/Web-Science-AE"><img src="https://img.shields.io/badge/CODE-0f766e?style=for-the-badge&logo=github&logoColor=white"></a>

### Tango with Django
`DJANGO` `REST`

Django web app with authentication, forms and REST endpoints.

<a href="https://github.com/RobinSpreckley/tango_with_django_project"><img src="https://img.shields.io/badge/CODE-0f766e?style=for-the-badge&logo=github&logoColor=white"></a>

<!-- ## ✦ hacks & side quests
### Hackathon name · Year
`TAG` `TAG`
One line on what you built or placed. Link the repo.
-->
