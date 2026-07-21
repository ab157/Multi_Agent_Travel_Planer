# Multi-Agent Travel Planner

A FastAPI-based travel planning application that uses a multi-agent LangGraph workflow to generate trip suggestions combining flight data, hotel recommendations, and a day-by-day itinerary.

## Overview

This project provides a simple web UI where users can describe a trip request such as:

- "Plan a 7-day Japan trip from India under 2 lakhs"
- "Create a 5-day Dubai trip with flights and hotels"
- "Suggest a budget-friendly travel plan for the USA"

The backend coordinates multiple agents to gather information and compose a final travel response.

## Features

- Interactive web interface for travel prompts
- Multi-agent planning flow with LangGraph
- Flight information lookup via AviationStack
- Hotel and travel research via Tavily
- Final itinerary generation using Groq LLMs
- Thread-based conversation support with PostgreSQL checkpointing
- PDF export support from the frontend

## Project Structure

- app.py: FastAPI application and API routes
- backend.py: LangGraph travel planning workflow
- tools/flight_tool.py: flight lookup and airport resolution logic
- tools/tavily_tool.py: web research integration
- templates/: HTML frontend templates
- static/: CSS and JavaScript assets

## Tech Stack

- Python
- FastAPI
- LangGraph
- LangChain
- Groq
- Tavily
- PostgreSQL

## Prerequisites

Make sure you have:

- Python 3.10+
- A PostgreSQL database
- API keys for:
  - Groq
  - Tavily
  - AviationStack
  - langsmith

## Environment Variables

Create a .env file in the project root with the following variables:

```env
GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
AVIATIONSTACK_API_KEY=your_aviationstack_api_key
DATABASE_URL=your_postgresql_connection_string
DEFAULT_ORIGIN_IATA=DEL
```

## Installation

1. Clone the repository
2. Create and activate a virtual environment
3. Install dependencies:

```bash
pip install -r requirements.txt
```

## Running the App

Start the FastAPI server:

```bash
python app.py
```

Then open:

```text
http://127.0.0.1:8000/
```

## API Endpoints

- GET /: homepage UI
- POST /api/travel: submit a travel prompt
- GET /health: health check

## Notes

- The application expects a valid database connection for LangGraph checkpointing.
- Some flight data may be unavailable depending on the API provider and request parameters.

## License

This project is licensed under the MIT License.
