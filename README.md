# League of Legends Analytics Platform 🎮⚔️

[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![Apache Kafka](https://img.shields.io/badge/Kafka-3.6+-231F20.svg)](https://kafka.apache.org/)
[![Apache Spark](https://img.shields.io/badge/Spark-3.5+-E25A1C.svg)](https://spark.apache.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791.svg)](https://www.postgresql.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Real-time analytics platform for League of Legends, processing match data and player statistics to uncover meta trends and performance insights.

## 🎯 Overview

This project demonstrates real-time stream processing and analytics for League of Legends:

- **Match Data Ingestion**: Riot Games API for comprehensive match history
- **Real-time Streaming**: Apache Kafka for high-throughput event processing
- **Stream Analytics**: Apache Spark for real-time win-rate calculations and meta analysis
- **Data Warehouse**: PostgreSQL for structured analytics storage
- **Visualization**: Interactive dashboards for champion performance, player stats, and meta trends

## 🏗️ Architecture

```
┌─────────────────┐     ┌─────────────┐     ┌──────────────┐
│  Riot Games API │────▶│    Kafka    │────▶│ Spark        │
│  (Match Data)   │     │   Cluster   │     │ Streaming    │
└─────────────────┘     └─────────────┘     └──────────────┘
                                                     │
            ┌────────────────────────────────────────┘
            ▼
┌─────────────────┐     ┌─────────────┐     ┌──────────────┐
│  Analytics DB   │◀────│  PostgreSQL │◀────│   Spark      │
│  (Dashboards)   │     │  (Warehouse)│     │  (Batch)     │
└─────────────────┘     └─────────────┘     └──────────────┘
```

## 🚀 Features

- **Champion Meta Analysis**: Track win rates, pick rates, and ban rates across patches
- **Player Performance Metrics**: KDA, CS/min, vision score tracking
- **Real-time Match Processing**: Live game event streaming and analysis
- **Ranked Distribution**: Player base analysis by tier and division
- **Item & Build Optimization**: Most effective item builds by champion and role
- **Patch Impact Analysis**: How balance changes affect the meta

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Data Source | Riot Games API |
| Streaming | Apache Kafka |
| Processing | Apache Spark (Streaming + Batch) |
| Database | PostgreSQL |
| Orchestration | Apache Airflow |
| Visualization | Streamlit |
| Infrastructure | Docker, Docker Compose |

## 📁 Project Structure

```
.
├── api/                     # Riot API integration
│   ├── client.py           # API client with rate limiting
│   ├── match_fetcher.py    # Match history ingestion
│   └── summoner_lookup.py  # Player profile retrieval
├── kafka/                   # Kafka producers and consumers
│   ├── producers/
│   │   └── match_events.py
│   └── consumers/
│       └── match_processor.py
├── spark/                   # Spark streaming jobs
│   ├── streaming/
│   │   └── live_metrics.py
│   └── batch/
│       └── champion_stats.py
├── dbt/                     # Data transformation models
│   └── models/
├── streamlit/               # Dashboard application
│   └── app.py
├── airflow/                 # DAGs for orchestration
│   └── dags/
├── docker-compose.yml       # Local stack
└── README.md
```

## 🚦 Quick Start

```bash
# Clone the repository
git clone https://github.com/CR7REX/gaming-telemetry-platform.git
cd gaming-telemetry-platform

# Set up Riot API key
export RIOT_API_KEY="your-api-key"

# Start the infrastructure
docker-compose up -d

# Fetch sample match data
python api/match_fetcher.py --summoner-name="Faker" --region=kr

# Run Spark analysis
spark-submit spark/batch/champion_stats.py

# Launch dashboard
streamlit run streamlit/app.py
```

## 📊 Key Metrics

- **Champion Win Rate**: By patch, tier, and role
- **Meta Shifts**: Pick/ban rate trends over time
- **Player KDA**: Kill/Death/Assist ratios by champion
- **Game Duration**: Average match length by patch
- **First Blood Impact**: Correlation with win rate
- **Objective Control**: Dragon/Baron control rates

## 🔧 Riot API Integration

This project uses the [Riot Games API](https://developer.riotgames.com/):

- **Rate Limiting**: Automatic request throttling
- **Caching**: Redis cache for frequently accessed data
- **Error Handling**: Retry logic for failed requests
- **Multi-region Support**: NA, EUW, KR, and more

## 🗺️ Roadmap

- [ ] Live match prediction using ML models
- [ ] Champion recommendation engine
- [ ] Player performance comparison tool
- [ ] Esports match analysis (LCK, LPL, LEC, LCS)
- [ ] Real-time draft phase analytics

## 📝 License

MIT License - see [LICENSE](LICENSE) for details.

---

*Analyzing the Rift, one match at a time* ⚔️📊
