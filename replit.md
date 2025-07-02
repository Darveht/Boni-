# DramaStream - Premium Video Streaming Application

## Overview

DramaStream is a modern, mobile-first video streaming application inspired by DramaBox but with an Uber-like design aesthetic. The application allows users to stream premium dramas, anime, and international series with features like offline downloads, multiple subscription tiers, and a clean, professional interface.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **UI Library**: Radix UI components with shadcn/ui styling system
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **State Management**: TanStack React Query for server state management
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Runtime**: Node.js with Express.js server
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL store

### Mobile-First Design
- **Responsive**: Optimized for mobile with max-width container (max-w-sm)
- **UI Pattern**: Bottom navigation with card-based content layout
- **Theme**: Uber-inspired design with clean, modern aesthetics
- **Color Scheme**: Supports both light and dark modes

## Key Components

### Authentication System
- **Provider**: Replit Auth integration
- **Flow**: OAuth 2.0 / OpenID Connect workflow
- **Session Storage**: PostgreSQL-backed sessions with 7-day TTL
- **User Management**: Automatic user creation and profile management

### Database Schema
- **Users**: Profile information, subscription tiers
- **Series**: Content metadata, ratings, genres
- **Episodes**: Individual episode data with streaming URLs
- **Watch History**: User progress tracking
- **Favorites**: User's saved content
- **Sessions**: Authentication session storage

### Video Streaming Features
- **Player**: Custom video player with progress tracking
- **Quality Control**: HD/4K support with quality selection
- **Offline Downloads**: For premium subscribers
- **Subtitles**: Multi-language subtitle support
- **Progress Sync**: Cross-device watch progress synchronization

### Subscription Management
- **Tiers**: Free (ad-supported), Monthly Premium, Annual Premium
- **Features**: Ad-free viewing, offline downloads, early access
- **Payments**: Integration ready for payment processing

## Data Flow

### Content Discovery
1. User browses featured/popular content on home screen
2. Series data fetched from `/api/series/featured` and `/api/series/popular`
3. Search functionality queries `/api/series/search` with real-time results
4. Content filtered by subscription tier and availability

### Video Playback
1. User selects episode from series detail page
2. Video player loads with episode metadata from `/api/episodes/:id`
3. Progress tracking updates via `/api/watch-progress`
4. Continue watching feature populated from watch history

### User Management
1. Authentication handled via `/api/auth/*` routes
2. User preferences and favorites managed through profile
3. Subscription status determines content access levels

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL connection
- **drizzle-orm**: Type-safe SQL toolkit and ORM
- **@tanstack/react-query**: Server state management
- **@radix-ui/***: Unstyled, accessible UI components
- **tailwindcss**: Utility-first CSS framework
- **wouter**: Minimalist routing for React

### Authentication
- **openid-client**: OpenID Connect client implementation
- **passport**: Authentication middleware
- **express-session**: Session management
- **connect-pg-simple**: PostgreSQL session store

### Development Tools
- **vite**: Build tool and development server
- **typescript**: Type safety and development experience
- **tsx**: TypeScript execution for Node.js

## Deployment Strategy

### Development Environment
- **Server**: Express.js with Vite middleware for HMR
- **Database**: Development database via DATABASE_URL
- **Authentication**: Replit Auth in development mode

### Production Build
- **Frontend**: Vite builds optimized React bundle to `dist/public`
- **Backend**: esbuild compiles Express server to `dist/index.js`
- **Static Assets**: Served from built frontend bundle
- **Environment**: Production environment variables required

### Environment Variables Required
- `DATABASE_URL`: PostgreSQL connection string
- `SESSION_SECRET`: Secret for session encryption
- `REPL_ID`: Replit environment identifier
- `ISSUER_URL`: OpenID Connect issuer URL

### Scaling Considerations
- Database connection pooling via Neon serverless
- Session storage in PostgreSQL for horizontal scaling
- CDN-ready static asset serving
- Mobile-optimized bundle sizes

## Changelog

Changelog:
- July 02, 2025. Initial setup

## User Preferences

Preferred communication style: Simple, everyday language.
