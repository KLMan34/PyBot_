# Chat Application

## Overview

This is a full-stack chat application built with React, TypeScript, Express, and Drizzle ORM. It features a modern iOS-inspired UI with shadcn/ui components, real-time messaging with an AI chatbot powered by OpenAI, and message search functionality.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for development and build process
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **UI Framework**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **Mobile-First**: Responsive design with iOS-inspired chat interface

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **External API**: OpenAI GPT-4o for AI chat responses
- **Session Management**: Built-in session handling with request logging

## Key Components

### Database Schema
- **Users Table**: Basic user authentication structure (id, username, password)
- **Messages Table**: Chat message storage with metadata (id, content, sender, timestamp, hasCode, codeLanguage)
- **Storage Layer**: Abstracted interface supporting both memory storage (development) and database persistence

### API Endpoints
- `GET /api/messages` - Retrieve recent messages with optional limit
- `GET /api/messages/search` - Search messages by content
- `POST /api/messages` - Send user message and receive AI response

### UI Components
- **MessageBubble**: Renders chat messages with code syntax highlighting
- **TypingIndicator**: Shows bot typing animation
- **CodeBlock**: Syntax-highlighted code blocks with copy functionality
- **Chat Interface**: iOS-style chat layout with search functionality

## Data Flow

1. **User Input**: User types message in textarea component
2. **Message Submission**: Frontend validates and sends message via POST request
3. **AI Processing**: Backend saves user message, sends to OpenAI API, receives response
4. **Response Handling**: Backend saves AI response and returns both messages
5. **UI Updates**: Frontend updates chat interface using React Query cache invalidation
6. **Search**: Real-time search through message history with debounced queries

## External Dependencies

### Core Dependencies
- **Database**: Neon PostgreSQL serverless database
- **AI Service**: OpenAI API for GPT-4o chat completions
- **UI Components**: Radix UI primitives for accessible components
- **Development**: Replit-specific plugins for development experience

### Authentication
- Basic session-based authentication structure is in place but not fully implemented
- Ready for extension with proper login/logout flow

## Deployment Strategy

- **Development**: Runs on Replit with hot reload via Vite
- **Production**: Builds static frontend and bundles backend with esbuild
- **Database**: Uses environment variable `DATABASE_URL` for PostgreSQL connection
- **Environment**: OpenAI API key configured via environment variables
- **Static Assets**: Frontend served from `/dist/public` after build

### Build Process
1. `npm run build` - Builds React frontend and bundles Express backend
2. `npm start` - Runs production server
3. `npm run dev` - Development mode with hot reload
4. `npm run db:push` - Pushes database schema changes

The application is designed to be easily deployable on various platforms while maintaining development efficiency on Replit.
