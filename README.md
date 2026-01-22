# Musicalitisim

<div align="center">
<a href="https://github.com/MasihOmar/Musicalitisim">
    <img alt="Musicalitisim banner" src="https://raw.githubusercontent.com/MasihOmar/Musicalitisim/main/frontend/assets/banner.png" width="800" />
</a>

<br/>
<br/>

<div align="center">
    <a href="https://github.com/MasihOmar/Musicalitisim">Project Home</a> |
    <a href="#documentation">Documentation</a> |
    <a href="#quick-start">Quick Start</a> |
    <a href="#contributing">Contributing</a>
</div>
</div>


<p align="center"><strong>A modern mobile-first music streaming app with an Expo React Native frontend and a Spring Boot REST API backend.</strong></p>


---

## Why Musicalitisim?

Musicalitisim is built to be a developer-friendly, extensible music streaming platform for personal and small-team projects. It emphasizes:

- Fast iteration with Expo for React Native
- A robust Java Spring Boot backend for streaming and metadata
- Simple configuration for local development and device testing
- Clear separation between frontend and backend so teams can iterate independently


## Key features

- User authentication and profile management
- Search (server-side with client-side fallback)
- Playlists, library browsing (artists, albums), and playlist management
- Audio streaming endpoints and player (mini player + full player)
- Network and server reachability checks with user-facing settings
- Configurable API URL for emulator and physical device development
- OpenAPI/Swagger support on the backend

---

## Tech stack

- Frontend: Expo + React Native, JavaScript, React Context
- Backend: Spring Boot (Java 17), Spring Web, Spring Data JPA, Spring Security
- Database: Microsoft SQL Server (production), H2 for development/runtime
- Build: npm (frontend), Maven (backend)

---

## Repository layout

- frontend/ — Expo React Native app
  - src/ — source code (screens, components, navigation, context, services)
  - package.json — dependencies & scripts
- restAPI/ — Spring Boot backend
  - src/main/java/... — controllers, services, persistence, stream handlers
  - src/main/resources/application.properties — defaults for storage and server port
  - pom.xml — Maven configuration

---

## Quick links

- Health check (backend): `/v1/api/health/ping`
- Frontend default Android emulator API URL: `http://10.0.2.2:8080`
- Swagger UI (backend): `http://localhost:8080/swagger-ui/index.html`

---

## Quick start

The following instructions will get you running locally with sensible defaults.

### Backend (Spring Boot)

Prerequisites

- Java 17+
- Maven 3.6+

Steps

1. Open a terminal and run:

```bash
cd restAPI
mvn clean package
mvn spring-boot:run
```

2. Verify the server is running:

```bash
# Health check
curl http://localhost:8080/v1/api/health/ping

# Swagger UI
# Open http://localhost:8080/swagger-ui/index.html in your browser
```

Notes

- Config is in `src/main/resources/application.properties`. For SQL Server, update JDBC URL and credentials.
- Default storage directories:
  - `${user.home}/MusicApp/songs/`
  - `${user.home}/MusicApp/coverArt/`


### Frontend (Expo)

Prerequisites

- Node 18+ (recommended)
- npm or yarn
- expo (optional) or use `npx expo`

Steps

```bash
cd frontend
npm install
npm run start
# or
npm run android
npm run ios
```

Notes

- The frontend stores and manages the API URL in AsyncStorage and defaults to `http://10.0.2.2:8080` for Android emulator.
- If using a physical device, set the API URL to your host machine IP, e.g. `http://192.168.1.XX:8080` and ensure the port is reachable.

---

## Configuration

- `frontend/src/services/api.js` contains helpers: `initApiConfig()`, `checkServerReachability()`, and `updateApiUrl()`.
- Backend properties are in `restAPI/src/main/resources/application.properties`.
- The backend also contains `target/classes/application.yaml` with an example configuration referencing SQL Server.

---

## Development notes

- Authentication lifecycle is handled by `frontend/src/context/AuthContext.js`.
- The MiniPlayer overlay is implemented in `frontend/src/components/MiniPlayer.js` and is rendered on top of navigators.
- Search falls back to local filtering if server results are missing or irrelevant.
- Streaming endpoints are defined under `restAPI` controllers, e.g. `SongController`.

---

## Suggested local workflow

1. Start the backend with `mvn spring-boot:run`.
2. Start Expo (`npm run start`) and run on emulator.
3. Use the Settings screen in the app to verify and update API URL.

---

## Contributing

Contributions are welcome. Suggested flow:

1. Fork the repo
2. Create a feature branch
3. Open a descriptive PR against the default branch

Please include tests for backend changes and component snapshots or simple behavior tests for critical frontend logic.

---

## Security & Credentials

- Remove any example credentials before deploying to production.
- If you publish this project, rotate database and security credentials.

---

## License

No license file is present in the repository. If you'd like to open-source the project, add a LICENSE file (e.g., MIT).

---

## Maintainer

MasihOmar — https://github.com/MasihOmar

---

*I created this README to match the professional layout you requested. If you want additional sections (badges, example screenshots, CI/CD setup, or an in-depth architecture diagram) I can add them. Commit this file to the repository now.*