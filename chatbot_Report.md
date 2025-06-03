# 🧠 S&P 500 Fact Chatbot – Project Report

## Overview

This project implements a **rule-based chatbot** designed to assist users in retrieving structured data about S&P 500 companies using natural language. The core objective is to simplify access to factual corporate data without memorizing database queries, using a combination of **regular expressions**, **Named Entity Recognition (NER)** with **spaCy**, and a **SQLite database** populated with real-world company data.

---

## Project Objectives

- Load and store structured data (e.g., company name, sector, HQ location, founding year) from a CSV into a SQLite database.
- Build a simple question-answering chatbot that:
  - Identifies user intent with regex and NER.
  - Extracts key information such as years or states.
  - Responds with relevant results pulled from the database.
- Provide a user interface through a simple terminal-based loop for interactive use.

---

## Tools & Environment

- **Environment**: Google Colab (Jupyter-like notebook)
- **Programming Language**: Python

### Libraries Used

- `pandas` – data handling
- `sqlite3` – database storage and querying
- `spacy` – Named Entity Recognition (NER)
- `re` – regex-based pattern matching
- *(Planned but not fully integrated: `Rasa NLU` for more advanced intent classification)*

---

## Data Preparation

- **Dataset**: `StockMarket_Description.csv` containing S&P 500 metadata.
- **Columns included**:
  - `symbol`
  - `security`
  - `gics_sector`
  - `gics_sub_industry`
  - `headquarters_location`
  - `date_added`
  - `cik`
  - `founded`

### Preprocessing

- Renamed columns for SQL compatibility.
- Stored the cleaned data in a SQLite database named `stockMarket_Description.db`.

---

## Chatbot Functionality

The chatbot matches user input against several intent patterns and responds accordingly.

### Intent Handlers

| **Intent**             | **Example**                                              | **Response Action**                                 |
|------------------------|----------------------------------------------------------|-----------------------------------------------------|
| HQ + Sector Search     | "Companies headquartered in Texas and Energy sector"     | Searches HQ and GICS sector columns                 |
| Founded Before Year    | "Which companies were founded before 1950?"              | Filters by `founded` column `< year`               |
| Founded After Year     | "Which companies were founded after 2000?"               | Filters by `founded` column `> year`               |
| By State               | "Show me companies headquartered in California"          | Extracts GPE location via spaCy                    |
| Sector Count           | "How many companies are in each sector?"                 | Groups companies by GICS sector                    |
| List All               | "List all companies"                                     | Lists all company names                            |
| Company Lookup         | "Tell me about Apple"                                    | Returns full company row from DB                   |

---

## Supporting Functions

- `query_db`: Helper function to execute and return SQL query results.
- `extract_year`: Uses spaCy NER to extract 4-digit years.
- `extract_state`: Extracts U.S. states or regions from input text using NER.
- Regex-based `respond` dispatcher to route inputs to the correct handler.

---

# Challenges & Limitations
- Regex-based intent matching is rigid and doesn't handle diverse phrasing well.
- Founding year format in the dataset was inconsistent and needed manual cleaning.
- The state/location matching is limited by how the HQ field is formatted (e.g., "San Jose, California").
- Rasa NLU was mentioned as a future improvement but not fully integrated due to time constraints.
- There is no persistent session or state-machine implementation, so multi-turn interactions aren't supported yet.

---

✅ Key Takeaways
- A simple rule-based chatbot with database integration can still be very useful for factual question answering.
- Preprocessing and proper column handling are essential for database reliability.
- spaCy’s NER and re are effective for extracting structured info from text.
- The foundation laid here supports easy expansion into:
- Full state-machine interaction flows
- Integration with Rasa NLU for machine-learned intent classification
- Web deployment or UI via Streamlit or Flask

---

# Sample Dialogue
```text
You: Which companies were founded before 1950?
Bot: Founded before 1950: Exxon Mobil, General Electric, Procter & Gamble

You: List companies headquartered in California and Technology sector
Bot: Matches: Apple, Intel, Cisco Systems

You: Tell me about Tesla
Bot: ('Tesla', 'Consumer Discretionary', 'Automobile Manufacturers', 'Palo Alto, California', '2010-07-01', '1318605', '2003')

```
