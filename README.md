# Capybara Adventure - Backend Server

Backend server for Capybara Adventure game, deployable to Railway.

## Features
- 🔐 Simple player authentication
- 🏆 Global leaderboards
- ⚔️ Real-time PvP matchmaking
- 💾 PostgreSQL persistence

## Deployment to Railway

### 1. Create a new project on Railway
Go to [railway.app](https://railway.app) and create a new project.

### 2. Add PostgreSQL
Click "New" → "Database" → "PostgreSQL"

### 3. Deploy the server
Connect this repo or:
```bash
# Install Railway CLI
npm install -g @railway/cli

# Login
railway login

# Link to project
railway link

# Deploy
railway up
```

### 4. Set environment variables
In Railway dashboard, set:
- `DATABASE_URL` - Auto-set if you added PostgreSQL
- `FRONTEND_URL` - Your deployed frontend URL
- `NODE_ENV` - `production`

### 5. Get your backend URL
Railway will give you a URL like `https://your-app.railway.app`

## Local Development

```bash
# Install dependencies
npm install

# Copy env example
cp .env.example .env

# Edit .env with your local PostgreSQL URL

# Run development server
npm run dev
```

## API Endpoints

### Player
- `POST /api/player/auth` - Login/Register
- `GET /api/player/:id` - Get profile
- `PUT /api/player/:id/stats` - Update stats

### Leaderboard
- `GET /api/leaderboard` - Get top scores
- `POST /api/leaderboard` - Submit score
- `GET /api/pvp/leaderboard` - Get PvP rankings

## Socket.io Events

### Client → Server
- `pvp:queue` - Join matchmaking
- `pvp:leave` - Leave queue
- `pvp:action` - Send combat action
- `pvp:result` - Report match result

### Server → Client
- `pvp:queued` - Confirmed in queue
- `pvp:match_found` - Match found!
- `pvp:opponent_action` - Opponent's action
- `pvp:match_end` - Match complete
- `pvp:opponent_disconnect` - Opponent left
