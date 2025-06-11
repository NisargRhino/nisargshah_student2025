---
layout: post
title: Stock Simulator Overview
categories: ['DevOps']
permalink: /stocks
menu: nav/tools_setup.html
toc: True
comments: True
---

# Bull & Byte: Stock Market Simulator for Financial Literacy



## Project Introduction

> "Investing education reimagined for the classroom."

**Bull & Byte** is a full-stack stock market simulator developed to teach high school students the fundamentals of financial literacy and trading. Designed for realism, educational depth, and classroom usability, it brings the world of investing to life with interactive charts, real-time prices, and intuitive interfaces.

---

## Backend System

### Flask-Based Financial Engine

The backend handles financial data processing, user authentication, transaction logic, and price caching.

#### Key Features:
- Live market data from **Yahoo Finance API**  
- Optimized caching to reduce rate-limit issues  
- Secure and trackable buy/sell transactions  
- Real-time profit/loss calculation per portfolio  
- Persistent user sessions and login system

---

### 📌 Sample Backend Code: Fetch Stock Data

```python
# /api/get_stock_data/<ticker>
from flask import Flask, jsonify
import yfinance as yf

@app.route("/api/get_stock_data/<ticker>", methods=["GET"])
def get_stock_data(ticker):
    stock = yf.Ticker(ticker)
    data = stock.history(period="1d", interval="1m")
    return jsonify({
        "price": stock.info.get('currentPrice'),
        "volume": stock.info.get('volume'),
        "dayHigh": stock.info.get('dayHigh'),
        "dayLow": stock.info.get('dayLow'),
        "fiftyTwoWeekHigh": stock.info.get('fiftyTwoWeekHigh'),
        "fiftyTwoWeekLow": stock.info.get('fiftyTwoWeekLow'),
    })
````

---

### 📌 Sample Backend Code: Add Stock to Portfolio

```python
# /api/add_stock (POST)
@app.route("/api/add_stock", methods=["POST"])
def add_stock():
    data = request.json
    user_id = data.get("user_id")
    ticker = data.get("ticker")
    quantity = int(data.get("quantity"))
    price = float(data.get("price"))

    # Save to DB (simplified)
    new_transaction = StockTransaction(
        user_id=user_id,
        ticker=ticker.upper(),
        quantity=quantity,
        price=price
    )
    db.session.add(new_transaction)
    db.session.commit()
    return jsonify({"status": "success", "message": f"Added {quantity} shares of {ticker}."})
```

---

## Frontend Interface

### Cross-Device Financial Playground

Built with HTML, CSS, and JavaScript for speed and responsiveness. The UI integrates educational and analytical features for an accessible and professional experience.

#### Key Features:

* Real-time charts powered by Chart.js and Matplotlib
* Interactive sidebars for instant stock switching
* Modal-based trading system for clean UX
* Financial term tooltips and guided tutorials
* Leaderboard and ranking logic (for classroom competition)

---

## Screenshots

### Main Dashboard View

![Stock Simulator Dashboard](../../mnt/data/Screenshot%202025-06-11%20at%2012.12.48%E2%80%AFPM.png)

Includes live NASDAQ data (e.g., AAPL), daily stats, and price history charts.

---

## Unique Qualities

* **Gamified Learning:** Turns investing into an engaging classroom experience
* **Data-Driven Architecture:** Uses live data, not static mockups
* **API-Efficient:** Built-in rate limiting + caching ensures stability
* **Classroom-Tested:** Stress-tested in real usage during live periods

---

## Roles and Contributions

* **Full-Stack Development:** Linked Flask backend to JS-based frontend
* **UI/UX Design:** Created all layouts, icons, and component flows
* **Project Leadership:** Managed planning, delegation, and agile sprints

---

## Events & Showcases

### Night at the Museum (N\@TM)

* Demonstrated live to educators, students, and families
* Implemented UI changes based on student feedback

### CTE Expo

* Presented to the principal and career pathway coordinators
* Approved for potential school-wide integration

---

## Real-World Impact

**Bull & Byte** is actively used across multiple CS periods at Del Norte High School. Students:

* Manage virtual portfolios
* Practice making informed trading decisions
* Learn about P/E ratios, volatility, and long-term vs. short-term returns

It supports **HyFlex Learning**, allowing students to experiment asynchronously and still compare performance in-class.

---

## GitHub Planning & Issue Tracker

Detailed architecture, future tasks, and team workflow are available here:
👉 [View on GitHub: Issue #109 – Stocks Overview](https://github.com/CSA-Coders-2025/Planning-Repository-Issue-House-/issues/109)

---

## Next Steps

* **Add Global Markets:** Pull data from London, Tokyo, and NSE APIs
* **Launch Mobile Version:** Port front-end to React Native
* **Add Portfolio Analytics:** Include Sharpe Ratio, beta values, risk assessment

> **Bull & Byte** is more than a simulator—it's a platform for building financial intuition, critical thinking, and tech skills in tomorrow's leaders.

```

---


