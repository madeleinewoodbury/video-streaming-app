# WebRTC Video Streaming App

A React-based video streaming application built with WebRTC technology for real-time video communication. The app features peer-to-peer video streaming with optional watermark functionality.

## Features

- **Real-time Video Streaming**: Uses WebRTC for low-latency peer-to-peer video communication
- **Watermark Toggle**: Optional watermark overlay on video streams
- **Responsive Design**: Built with Tailwind CSS for mobile and desktop compatibility
- **Stream Controls**: Start/stop streaming with intuitive button controls
- **Connection Monitoring**: Real-time connection state tracking and logging


## Prerequisites

- Node.js (v16 or higher)
- **Required**: The FastAPI backend must be running for video streaming functionality
  - **Backend Repository**: [video-streaming-api](https://github.com/madeleinewoodbury/video-streaming-api)
  - The API should be accessible at `http://localhost:8000`

## Installation

1. Clone the repository:
```bash
git clone https://github.com/madeleinewoodbury/video-streaming-app.git
cd video-streaming-app
```

2. Install dependencies:
```bash
npm install
```

3. **Start the backend API first** (see backend repo for instructions)

4. Start the development server:
```bash
npm run dev
```

The app will be available at `http://localhost:3000`

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## Usage

**Important**: Ensure the FastAPI backend is running at `http://localhost:8000` before using the app.

1. Open the application at `http://localhost:3000`
2. Toggle the watermark option if desired (only available when not streaming)
3. Click "Start Video Stream" to begin streaming
4. Click "Stop Video Stream" to end the session

### Development Workflow

1. **Terminal 1**: Start the FastAPI backend
   ```bash
   cd video-streaming-api
   uvicorn main:app --reload --host 0.0.0.0 --port 8000
   ```

2. **Terminal 2**: Start the React frontend
   ```bash
   cd video-streaming-app  
   npm run dev
   ```

## API Endpoints

The app expects the following backend endpoints:

- `POST /api/offer` - WebRTC offer/answer exchange
- `POST /api/offer?watermark=True` - WebRTC offer with watermark enabled
- `POST /api/close` - Close streaming connection

## Browser Compatibility

This application requires a modern browser with WebRTC support:
- Chrome 56+
- Firefox 51+
- Safari 11+
- Edge 79+

## Architecture

### Technology Stack
- **Frontend**: React 18 with Vite
- **Styling**: Tailwind CSS
- **Icons**: React Icons
- **WebRTC**: Native browser WebRTC APIs
- **Build Tool**: Vite for fast development and building

### Key Components
- **Home.jsx**: Main video streaming interface
- **WebRTC Integration**: Handles peer connection establishment and media streaming
- **Proxy Configuration**: Vite proxy routes `/api/*` requests to backend

## Related Projects

**Backend API**: https://github.com/madeleinewoodbury/video-streaming-api  
FastAPI server providing WebRTC signaling and video processing with motion detection.

## Troubleshooting

### Common Issues

**"Failed to fetch" errors:**
- Ensure the backend API is running on port 8000
- Check that both frontend and backend are on the same network

**Camera not working:**
- Grant camera permissions in your browser
- Ensure no other applications are using the camera
- Check browser developer tools for WebRTC errors

**Connection failures:**
- Verify backend health: `curl http://localhost:8000/health`
- Check browser console for detailed error messages

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
