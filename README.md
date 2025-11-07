# Amplitude API Connection

This repository explores and documents two approaches for extracting data from the Amplitude Analytics API:

1) A **Python-scripted extraction pipeline**
2) A **Low/no-code pipeline** using Airbyte

The diagrams below represent the conceptual architecture of both paths and how data moves through the ecosystem.

---
## Why do we want to do this?

This Amplitude is what The Information Lab website runs through. Looking at the data from this website can be extremely beneficial for sales and further knowledge about the company.

We are able to see information about who visits the website and what blogs or events they look at. To help see what areas are of most interest to site visitors.
---

## Extraction Architecture (Amplitude → Transformation → Destination)

![Extraction Architecture](https://github.com/Alfie-King/airbyte-api/blob/main/images/Amplitude%20API.png)

## Code Architecture (Python script approach)

![Code Architecture](https://github.com/Alfie-King/airbyte-api/blob/main/images/Code%20diagram.png)

---

## Why would you choose a Python script vs Airbyte?

Airbyte is excellent at standardized, “cookie-cutter” ELT pipelines.

However — Python can be a better fit when:

| Reason | Why it matters |
|--------|----------------|
| **Unusual endpoints or custom API parameters** | Many marketing / product analytics APIs (Amplitude included) expose complex query params that GUI connectors don’t surface fully |
| **Dynamic parameterization** | Some endpoints need looping over dates, events, pagination, cursor tokens, or rolling windows that are awkward or slow to model in a UI connector |
| **Full control over retries / rate limiting** | Amplitude rate limits aggressively — Python lets you control backoff logic exactly |
| **Transform while extracting** | You can merge, enrich, flatten JSON, deduplicate etc. *before landing* into a warehouse |
| **Version-controlled logic** | Code is auditable and follows software lifecycle — PRs, diff review, testing |
| **Connectors don’t exist yet** | If Airbyte doesn’t have a stable connector for your exact model or API variant, code wins immediately |
| **Price** | Python has a lower run cost than Airbyte as the process will be built in house |

### Practical summary

> Airbyte = fastest setup, easiest maintenance, great for common SaaS / DB sources  
> Python = best when control, customization, and correctness matter more than speed of initial setup

Many orgs run both in parallel — Airbyte handles “normal” sources, while Python handles “edge case” API data.

---

## Status

🚧 **Work in progress**  
This is an active experimentation repo — more code, examples, and patterns coming.

---

## Contributions

PRs, questions, and opinions are welcome.  
Please open an Issue if you have suggestions.
