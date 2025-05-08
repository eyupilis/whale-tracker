# Whale Tracker

Whale Tracker is a real-time monitoring application for tracking large USDT transfers (over 100,000 USDT) on the Ethereum blockchain. This project includes both a backend API and a frontend user interface.

## Features

- **Real-time Tracking** - Monitor large USDT transfers as they happen
- **Detailed Analytics** - View transaction details, statistics, and trends
- **Filtering & Pagination** - Search and filter transactions by value, address, etc.
- **Responsive UI** - Mobile-friendly design that works on all devices
- **WebSocket Support** - Real-time updates delivered instantly to the UI

## Tech Stack

### Backend
- Python 3.9+
- FastAPI - Web framework
- web3.py - Ethereum blockchain interaction
- WebSockets - Real-time data streaming
- Pydantic - Data validation

### Frontend
- React 18
- React Query - Data fetching and caching
- Chart.js - Data visualization
- Tailwind CSS - Styling
- WebSocket - Real-time updates

### Infrastructure
- Docker - Containerization
- Docker Compose - Container orchestration

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/)
- [Node.js](https://nodejs.org/) (for local development only)
- [Python 3.9+](https://www.python.org/downloads/) (for local development only)
- An Ethereum node provider API key (e.g., [Infura](https://infura.io/) or [Alchemy](https://www.alchemy.com/))

## Setup & Installation

### Using Docker (Recommended)

1. Clone the repository:
   ```bash
   git clone https://github.com/eyupilis/whale-tracker.git
   cd whale-tracker
   ```

2. Create a `.env` file in the `backend` directory:
   ```bash
   cp backend/.env.example backend/.env
   ```

3. Edit the `.env` file to add your Ethereum provider API key:
   ```
   ETHEREUM_PROVIDER_URL=https://mainnet.infura.io/v3/YOUR_INFURA_KEY
   ```

4. Build and start the containers:
   ```bash
   docker-compose up -d
   ```

5. Access the application:
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:8000
   - API Documentation: http://localhost:8000/docs

### Local Development Setup

#### Backend

1. Navigate to the backend directory:
   ```bash
   cd whale-tracker/backend
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create and configure `.env` file:
   ```bash
   cp .env.example .env
   # Edit .env to add your Ethereum provider API key
   ```

5. Run the backend server:
   ```bash
   uvicorn main:app --reload
   ```

#### Frontend

1. Navigate to the frontend directory:
   ```bash
   cd whale-tracker/frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```

## API Endpoints

- `GET /api/transactions` - Get a paginated list of transactions
- `GET /api/transactions/{tx_hash}` - Get details of a specific transaction
- `GET /api/stats` - Get overall transaction statistics
- `WebSocket /api/ws` - WebSocket endpoint for real-time updates

## Configuration Options

### Backend Environment Variables

- `ETHEREUM_PROVIDER_URL` - URL for the Ethereum node provider
- `ETHEREUM_NETWORK` - Network to connect to (mainnet, goerli, etc.)
- `USDT_CONTRACT_ADDRESS` - Address of the USDT contract to monitor
- `TRANSFER_THRESHOLD` - Minimum value in USDT to track (default: 100000)
- `API_HOST` - Host to bind the API server (default: 0.0.0.0)
- `API_PORT` - Port for the API server (default: 8000)
- `CORS_ORIGINS` - Allowed origins for CORS (default: http://localhost:3000)

## Multi-chain Support (Future Enhancement)

The current implementation focuses on Ethereum, but the architecture is designed to be extended to support additional chains:

1. **Supported Networks** (Future):
   - Binance Smart Chain (BSC)
   - Polygon
   - Arbitrum
   - Optimism

2. **Implementation Strategy**:
   - Abstract blockchain provider interface
   - Chain-specific adapters
   - Factory pattern for blockchain services

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.