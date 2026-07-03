# PokeBloom
Pokebloom is an 8-bit-style, single-player creature-collecting RPG. Players roam a pixel-art overworld, trigger wild encounters in tall grass and other zones, catch and train creatures, manage a party and item inventory, and battle their way through eight gym leaders to become champion.

## Tech Stack

- **Game engine:** Phaser 3 + TypeScript + Vite
- **UI:** React (mounted around the Phaser canvas)
- **Backend:** Node.js + Express (TypeScript)
- **Real-time:** Socket.io (server-authoritative battle sequencing)
- **Database:** PostgreSQL
- **ORM:** Prisma
- **External data:** PokeAPI (species/move data and sprites, cached locally)

## Prerequisites

Make sure you have the following installed before setting up the project:

- [Node.js](https://nodejs.org/) v18 or higher
- [npm](https://www.npmjs.com/) v9 or higher (comes with Node)
- [PostgreSQL](https://www.postgresql.org/download/) v14 or higher, running locally or accessible remotely
- [Git](https://git-scm.com/)

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/pokedale.git
cd pokedale
```

### 2. Set up the backend

```bash
cd server
npm install
```

Create a `.env` file in the `server/` directory:

```bash
cp .env.example .env
```

Fill in your environment variables:

```env
DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/pokedale?schema=public"
PORT=4000
JWT_SECRET="your-secret-here"
CLIENT_URL="http://localhost:5173"
```

Run Prisma migrations to set up your database schema:

```bash
npx prisma migrate dev
```

(Optional) Seed the database with base Pokémon/move/item data pulled from PokeAPI:

```bash
npm run seed
```

Start the backend dev server:

```bash
npm run dev
```

The API and Socket.io server should now be running on `http://localhost:4000`.

### 3. Set up the frontend

Open a new terminal window/tab:

```bash
cd client
npm install
```

Create a `.env` file in the `client/` directory:

```bash
cp .env.example .env
```

```env
VITE_API_URL="http://localhost:4000"
VITE_SOCKET_URL="http://localhost:4000"
```

Start the frontend dev server:

```bash
npm run dev
```

The game should now be running at `http://localhost:5173`.

## Available Scripts

**Backend (`server/`)**
| Command | Description |
|---|---|
| `npm run dev` | Start Express server in watch mode |
| `npm run build` | Compile TypeScript to `dist/` |
| `npm start` | Run compiled production build |
| `npx prisma studio` | Open a GUI to browse/edit the database |
| `npx prisma migrate dev` | Run pending migrations |
| `npm run seed` | Populate DB with PokeAPI-derived data |

**Frontend (`client/`)**
| Command | Description |
|---|---|
| `npm run dev` | Start Vite dev server |
| `npm run build` | Build production assets |
| `npm run preview` | Preview production build locally |

## Roadmap

- [ ] Overworld movement, tilemap, and encounter zones
- [ ] Turn-based battle system (server-authoritative via Socket.io)
- [ ] Catching mechanics and party/PC box management
- [ ] Item inventory (berries, potions, evolution stones)
- [ ] Evolution (level-based and item-based)
- [ ] First gym leader and badge system
- [ ] Remaining 7 gyms + champion route
