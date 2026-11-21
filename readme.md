# CodeMeet - Real-time Code Editor with Video Chat

CodeMeet is a collaborative coding room. Join the same room ID and everyone can edit code, chat, draw on a shared whiteboard and talk over a video call, all in real time.

## Features

- **Shared code editor**: built on Monaco and synced live over Socket.IO
- **Run code**: JavaScript, Python, Java and C++, using the [Piston API](https://github.com/engineer-man/piston)
- **Video calls**: peer-to-peer WebRTC (simple-peer), with Socket.IO for signaling
- **Whiteboard**: a shared canvas for sketching ideas
- **Chat**: in-room text messages
- **Rooms**: create a room or join one by ID, and download your code as a file

## Tech Stack

| Layer    | Tech                                                      |
|----------|-----------------------------------------------------------|
| Frontend | React 18, Vite, Tailwind CSS, Monaco Editor, React Router |
| Realtime | Socket.IO, WebRTC (simple-peer)                           |
| Backend  | Node.js, Express                                          |

## Project Structure

```
CodeMeet/
├── backend/
│   ├── index.js               # Express + Socket.IO server; also serves frontend/dist
│   ├── codeCollaboration.js   # Code sync, chat and code execution
│   ├── videoCallNew.js        # WebRTC signaling
│   └── whiteboard.js          # Whiteboard sync
├── frontend/
│   └── src/
│       ├── components/        # CodeEditor, Chat, Whiteboard, RoomSidebar
│       ├── hooks/             # App state, rooms, socket connection
│       ├── services/          # Socket and storage services
│       ├── Homepage.jsx
│       ├── VideoCallV2.jsx
│       └── WhiteboardPage.jsx
└── package.json               # Root scripts
```

## Getting Started

**You'll need:** Node.js 18 or later and npm.

```bash
# Install dependencies (postinstall also installs backend and frontend)
npm install

# Build the frontend
npm run build

# Start the server
npm start
```

Then open **http://localhost:5000**.

### Development

```bash
npm run dev
```

This starts the backend (nodemon) and the Vite dev server together.

## Configuration

| Variable   | Default | Description                                    |
|------------|---------|------------------------------------------------|
| `PORT`     | `5000`  | Server port                                    |
| `NODE_ENV` | –       | Set to `development` to turn on `/debug/rooms` |

## Endpoints

- `GET /health`: server status, active connections and uptime
- `GET /debug/rooms`: video room state (development only)

## License

ISC
