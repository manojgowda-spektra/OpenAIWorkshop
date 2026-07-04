# Fraud Detection Workflow Visualizer

A modern React application for visualizing and managing fraud detection workflows in real-time. Built with Vite, React, Material-UI, and React Flow.

## Features

- 🔄 Real-time workflow visualization
- 🎯 Interactive workflow controls
- 📊 Live event logging
- 👤 Human-in-the-loop decision making
- 🔌 WebSocket-based real-time updates
- 🎨 Material-UI based responsive design
- 📈 React Flow powered workflow graphs

## Tech Stack

- **Framework**: React 19.2
- **Build Tool**: Vite 7.2
- **UI Library**: Material-UI (MUI) 7.3
- **Graph Visualization**: React Flow 11.11
- **State Management**: React Hooks
- **Real-time Communication**: WebSocket

## Prerequisites

- Node.js 22+ (LTS)
- npm 9+ or newer

## Getting Started

### Installation

1. Clone the repository
2. Navigate to the project directory:

   ```bash
   cd agentic_ai/workflow/fraud_detection/ui
   ```

3. Install dependencies:

   ```bash
   npm install
   ```

4. Copy the environment file:

   ```bash
   cp .env.example .env
   ```

5. Configure your environment variables in `.env` if needed

### Development

Start the development server:

```bash
npm run dev
```

The application will open at `http://localhost:3000`

### Build

Build for production:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

### Docker

Build and run the application in a Docker container:

```bash
# Build the Docker image
docker build -t fraud-detection-ui:latest .

# Run the container
docker run -p 3000:3000 fraud-detection-ui:latest

# Run with custom backend URL
docker run -p 3000:3000 \
  -e VITE_API_BASE_URL=http://your-backend:8001 \
  -e VITE_WS_URL=ws://your-backend:8001/ws \
  fraud-detection-ui:latest
```

The Docker image uses a multi-stage build with:

- **Build stage**: Node.js 22 Alpine with all dependencies
- **Production stage**: Node.js 22 Alpine serving with `serve`
- **Security**: Runs as non-root user (nodejs:1001)
- **Port**: Exposes port 3000
- **Health check**: Built-in health monitoring

### Linting

Run ESLint:

```bash
npm run lint
```

Fix linting issues automatically:

```bash
npm run lint:fix
```

## Project Structure

```text
ui/
├── src/
│   ├── components/       # React components
│   │   ├── AnalystDecisionPanel.jsx
│   │   ├── ControlPanel.jsx
│   │   ├── CustomNode.jsx
│   │   ├── EventLog.jsx
│   │   └── WorkflowVisualizer.jsx
│   ├── hooks/           # Custom React hooks
│   │   └── useWebSocket.js
│   ├── utils/           # Utility functions
│   │   ├── api.js
│   │   ├── helpers.js
│   │   └── uiHelpers.jsx
│   ├── constants/       # Application constants
│   │   ├── config.js
│   │   └── workflow.js
│   ├── theme/           # MUI theme configuration
│   │   └── index.js
│   ├── App.jsx          # Main application component
│   ├── main.jsx         # Application entry point
│   └── index.css        # Global styles
├── public/              # Static assets
├── .env                 # Environment variables
├── .env.example         # Environment variables example
├── .eslintrc.cjs        # ESLint configuration
├── .gitignore          # Git ignore rules
├── index.html          # HTML template
├── jsconfig.json       # JavaScript configuration
├── package.json        # Project dependencies
├── vite.config.js      # Vite configuration
└── README.md           # This file
```

## Path Aliases

The project uses path aliases for cleaner imports:

- `@/` → `src/`
- `@components/` → `src/components/`
- `@hooks/` → `src/hooks/`
- `@utils/` → `src/utils/`
- `@theme/` → `src/theme/`
- `@constants/` → `src/constants/`

Example:

```javascript
import WorkflowVisualizer from '@components/WorkflowVisualizer';
import { useWebSocket } from '@hooks/useWebSocket';
import theme from '@theme';
```

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `VITE_API_BASE_URL` | Backend API URL | `http://localhost:8001` |
| `VITE_WS_URL` | WebSocket URL | `ws://localhost:8001/ws` |
| `VITE_APP_TITLE` | Application title | `Fraud Detection Workflow Visualizer` |

## API Integration

The application connects to a backend API running on `http://localhost:8001` by default. The following endpoints are used:

- `GET /api/alerts` - Fetch available alerts
- `POST /api/workflow/start` - Start a workflow
- `POST /api/workflow/decision` - Submit analyst decision
- `WS /ws` - WebSocket connection for real-time updates

## Components

### Main Components

- **App.jsx** - Main application component, orchestrates all child components
- **WorkflowVisualizer** - Displays the workflow graph with real-time state updates
- **ControlPanel** - Alert selection and workflow control interface
- **AnalystDecisionPanel** - Human-in-the-loop decision making interface
- **EventLog** - Real-time event logging display
- **CustomNode** - Custom node component for workflow graph

### Hooks

- **useWebSocket** - Manages WebSocket connections with automatic reconnection

## Development Guidelines

### Code Style

- Use functional components with hooks
- Follow ESLint rules
- Use path aliases for imports
- Add JSDoc comments for functions
- Keep components small and focused

### Adding New Components

1. Create component in `src/components/`
2. Export from the component file
3. Import using path alias: `import Component from '@components/Component'`

### Adding New Constants

1. Add constants to appropriate file in `src/constants/`
2. Export named exports
3. Import where needed: `import { CONSTANT } from '@constants/config'`

## Troubleshooting

### WebSocket Connection Issues

- Ensure backend server is running
- Check `VITE_WS_URL` in `.env`
- Check browser console for connection errors

### Build Issues

- Clear node_modules and reinstall: `rm -rf node_modules && npm install`
- Clear Vite cache: `rm -rf node_modules/.vite`

## License

See the main project LICENSE file.

## Contributing

Please read the main project CONTRIBUTING guidelines.
