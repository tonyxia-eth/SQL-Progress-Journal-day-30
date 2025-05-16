# SQL-Progress-Journal-day-30

# Subway Card Swipe Schema – CS50 SQL Journey

🔧 **Focus**: SQL Schema Design, Table Constraints, Error Handling, and Troubleshooting  
🛠️ **Tool**: SQLite (via GitHub.dev)

---

## 🧠 What I Did

Today, I built a full relational schema to track subway card swipes, including:

- 💳 `cards`: Unique identifiers for swipe cards.
- 🚉 `stations`: Stations with enforced uniqueness and line info.
- 🎫 `swipes`: Log of rider interactions (enter/exit/deposit), time, and amount, with full foreign key integrity.

---

## 🗃️ Final Schema

```sql
CREATE TABLE "cards" (
    "id" INTEGER,
    PRIMARY KEY ("id")
);

CREATE TABLE "stations" (
    "id" INTEGER,
    "name" TEXT NOT NULL UNIQUE,
    "line" TEXT NOT NULL,
    PRIMARY KEY ("id")
);

CREATE TABLE "swipes" (
    "id" INTEGER,
    "rider_id" INTEGER,
    "card_id" INTEGER,
    "station_id" INTEGER,
    "type" TEXT NOT NULL CHECK ("type" IN ('enter', 'exit', 'deposit')),
    "datetime" NUMERIC NOT NULL DEFAULT CURRENT_TIMESTAMP,
    "amount" NUMERIC NOT NULL CHECK("amount" != 0),
    PRIMARY KEY ("id"),
    FOREIGN KEY ("rider_id") REFERENCES "cards" ("id"),
    FOREIGN KEY ("station_id") REFERENCES "stations" ("id")
);

🔍 What I Learned
How to use CHECK constraints for cleaner, validated data input.

How to reference foreign keys properly (not just column names).

How to drop tables safely using DROP TABLE IF EXISTS.

How to read error messages and identify common syntax issues like mismatched quotes or missing commas.

That CTRL+C doesn't always exit SQLite and how to work around that on GitHub.dev.

🧱 Real-World Relevance
This schema could power basic public transit card systems, including fare tracking, entry/exit logs, and payment deposits.

🧠 Next Steps
Insert mock data to test logic.

Create queries to summarize rider behavior, revenue, or station usage.

Connect schema to a lightweight frontend or Power BI/Tableau dashboard.

🔁 Reflection
Even while feeling under the weather, I showed up, solved real errors, and left the schema cleaner than I found it.

#SQL #Databases #DataEngineering #100DaysOfSQL #MenInTech
