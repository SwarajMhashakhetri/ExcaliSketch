# ExcaliSketch - Collaborative Drawing Platform

A real-time collaborative whiteboarding application built with modern web technologies, inspired by Excalidraw. Users can create, edit, and collaborate on drawings in real-time with multiple drawing tools and features.

## 🚀 Live Demo

- **Excali-Sketch**: [https://excali-sketch-frontend-omni.vercel.app/](https://excali-sketch-frontend-omni.vercel.app/)

## ✨ Features

### Core Drawing Tools
- **Shape Tools**: Rectangle, Ellipse, Diamond, Line, Arrow
- **Freehand Drawing**: Smooth pen tool for freeform drawing
- **Text Tool**: Add and edit text with custom positioning
- **Eraser Tool**: Remove shapes and drawings
- **Selection Tool**: Select, move, resize, and rotate shapes

### Real-time Collaboration
- **Live Synchronization**: See changes from other users instantly
- **Room-based System**: Create and join drawing rooms
- **Multi-user Support**: Multiple users can draw simultaneously
- **WebSocket Communication**: Low-latency real-time updates

### Advanced Features
- **Shape Manipulation**: Resize, rotate, and move shapes with intuitive handles
- **Color Customization**: Advanced color picker with custom color support
- **Shape Selection**: Click to select and modify individual shapes
- **Keyboard Shortcuts**: Quick tool switching (1-9 keys)
- **Responsive Design**: Works on desktop and mobile devices

### User Management
- **Authentication**: JWT-based user authentication
- **User Registration/Login**: Secure account creation and management
- **Room Management**: Create, join, and manage drawing rooms
- **Dashboard**: User dashboard for managing rooms and drawings

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 15.3.1 with React 19
- **Language**: TypeScript 5.7.3
- **Styling**: Tailwind CSS 3.4.17
- **UI Components**: Radix UI primitives
- **Animations**: Framer Motion 12.5.0
- **State Management**: Zustand 5.0.3
- **Canvas API**: HTML5 Canvas for drawing operations
- **WebSocket**: Native WebSocket API for real-time communication

### Backend
- **Runtime**: Node.js with Express.js 4.21.2
- **Language**: TypeScript 5.7.3
- **Database**: PostgreSQL with Prisma ORM 6.3.1
- **Authentication**: JWT (jsonwebtoken 9.0.2)
- **Password Hashing**: bcrypt 5.1.1
- **WebSocket**: ws 8.18.0 for real-time communication
- **Validation**: Zod 3.24.1 for input validation
- **Rate Limiting**: express-rate-limit 7.5.0
- **Logging**: Morgan 1.10.0 with rotating file streams

### DevOps & Deployment
- **Package Manager**: pnpm 8.15.6
- **Build System**: Turbo 2.4.2 (monorepo)
- **Frontend Hosting**: Vercel
- **Backend Hosting**: Vercel
- **Database**: PostgreSQL (hosted)
- **Environment**: Production-ready with CORS, rate limiting, and security headers

### Development Tools
- **Linting**: ESLint 9.20.0 with custom configurations
- **Code Formatting**: Prettier 3.5.0
- **Type Checking**: TypeScript strict mode
- **Monorepo**: Workspace-based package management

## 🏗️ Architecture

### Monorepo Structure
```
Excali-Sketch/
├── apps/
│   ├── ExcaliSketch/          # Next.js frontend application
│   └── backend/               # Express.js backend API
├── packages/
│   ├── ui/                    # Shared UI components
│   ├── eslint-config/         # Shared ESLint configurations
│   ├── tailwind-config/       # Shared Tailwind configuration
│   └── typescript-config/     # Shared TypeScript configurations
└── turbo.json                 # Turbo build configuration
```

### Database Schema
- **Users**: User authentication and profile data
- **Rooms**: Drawing room management and metadata
- **RoomState**: Real-time drawing state persistence
- **Chat**: Optional chat functionality for rooms

### Real-time Communication Flow
1. User authenticates via JWT token
2. WebSocket connection established with authentication
3. User joins a drawing room
4. Drawing operations broadcast to all room participants
5. State changes persisted to database
6. New users receive current room state upon joining

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ 
- pnpm 8.15.6+
- PostgreSQL database

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/SwarajMhashakhetri/ExcaliSketch.git
   cd Excali-Sketch
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Set up environment variables**
   
   Create `.env` files in both `apps/ExcaliSketch/` and `apps/backend/`:
   
   **Frontend (.env.local)**:
   ```env
   NEXT_PUBLIC_BACKEND_URL=http://localhost:5000
   NEXT_PUBLIC_WS_URL=ws://localhost:5000
   ```

   **Backend (.env)**:
   ```env
   DATABASE_URL="postgresql://username:password@localhost:5432/excalisketch"
   USER_JWT_SECRET="your-jwt-secret"
   PORT=5000
   ```

4. **Set up the database**
   ```bash
   cd apps/backend
   npx prisma generate
   npx prisma db push
   ```

5. **Start the development servers**
   ```bash
   # Start both frontend and backend
   pnpm dev
   
   # Or start individually
   pnpm --filter ExcaliSketch dev
   pnpm --filter backend dev
   ```

6. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

## 📱 Usage

### Creating a Drawing
1. Sign up or log in to your account
2. Click "Start Drawing" from the dashboard
3. Select drawing tools from the toolbar
4. Draw shapes, add text, or use freehand drawing
5. Share the room link with collaborators

### Collaboration
1. Share the room URL with team members
2. All participants can draw simultaneously
3. Changes appear in real-time for all users
4. Use different colors to identify different contributors

### Keyboard Shortcuts
- `1` - Selection tool
- `2` - Rectangle tool
- `3` - Diamond tool
- `4` - Ellipse tool
- `5` - Arrow tool
- `6` - Line tool
- `7` - Freehand drawing
- `8` - Text tool
- `9` - Eraser tool

## 🔧 API Endpoints

### Authentication
- `POST /user/signup` - User registration
- `POST /user/signin` - User login
- `GET /user/profile` - Get user profile

### Rooms
- `POST /room/create` - Create a new drawing room
- `GET /room/:id` - Get room details and drawing state
- `GET /room/user/:userId` - Get user's rooms

### WebSocket Events
- `auth` - Authenticate WebSocket connection
- `join_room` - Join a drawing room
- `leave_room` - Leave current room
- `message` - Send drawing updates

## 🚀 Deployment

### Frontend (Vercel)
1. Connect your GitHub repository to Vercel
2. Set environment variables in Vercel dashboard
3. Deploy automatically on push to main branch

### Backend (Vercel)
1. Configure Vercel for Node.js
2. Set environment variables
3. Deploy with automatic builds

### Database
- Use a managed PostgreSQL service (e.g., Neon, Supabase, or Railway)
- Update `DATABASE_URL` in production environment

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Swaraj Mhashakhetri**
- LinkedIn: [https://www.linkedin.com/in/swaraj-mhashakhetri/](https://www.linkedin.com/in/swaraj-mhashakhetri/)
- GitHub: [https://github.com/SwarajMhashakhetri](https://github.com/SwarajMhashakhetri)

## 🙏 Acknowledgments

- Inspired by [Excalidraw](https://excalidraw.com/)
- Built with modern web technologies and best practices
- Special thanks to the open-source community for the amazing tools and libraries

---

**Note**: This is a full-stack application demonstrating real-time collaboration, modern web development practices, and scalable architecture patterns.
