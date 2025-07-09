# SEVA - Ambulance Aggregator & Emergency Assistance Platform

## Overview

SEVA is a comprehensive emergency response platform designed for India, combining ambulance aggregation, real-time tracking, hospital recommendations, and AI-powered first aid assistance. The application serves as a bridge between emergency situations and healthcare providers, offering a seamless experience for both patients and ambulance drivers.

## Recent Changes (January 2025)

✓ **Hackathon Demo Features Implemented**
- Added simulated ambulance movement for indoor demo environments
- Implemented driver panel with real-time location sharing
- Added Firebase integration for live tracking (with fallback for demo mode)
- Enhanced mobile-responsive design with emergency color scheme
- Separate login systems for drivers and patients
- Auto-simulation of ambulance movement starting from Delhi coordinates (28.6139, 77.2090)

✓ **Core Platform Features**
- Multi-page React application with full navigation
- Real-time ambulance tracking with Google Maps integration
- AI-powered first aid assistance using Google Gemini API
- Hospital recommendation system with location-based search
- Driver panel for ambulance operators with simulation capabilities
- Separate authentication flows for patients and drivers

✓ **Technical Improvements**
- Fixed TypeScript compilation errors in storage layer
- Added proper error handling for missing API keys
- Implemented demo modes for Firebase and Google Maps
- Added comprehensive SEO meta tags and social media sharing
- Enhanced mobile navigation with bottom tab bar
- Fixed homepage UI text visibility issues
- Updated Gemini API to use correct model (gemini-2.5-flash)
- Implemented exact ambulance movement simulation as specified

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for development and production builds
- **UI Framework**: Tailwind CSS with custom emergency color scheme
- **Component Library**: Radix UI primitives via shadcn/ui
- **State Management**: TanStack Query for server state and React hooks for local state
- **Routing**: Wouter for client-side routing
- **Styling**: CSS custom properties with emergency-themed color palette (red, blue, white)

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (@neondatabase/serverless)
- **API Design**: RESTful endpoints with proper error handling
- **Development**: Hot reloading with Vite middleware integration

### Key Components

#### Database Schema
- **Users**: Stores user information with roles (patient/driver)
- **Ambulances**: Vehicle details, driver info, location, and availability status
- **Emergency Requests**: Request management with status tracking
- **Hospitals**: Hospital information with location and specialties

#### Core Features
1. **Home Dashboard**: Emergency contacts and quick access to services
2. **Ambulance Finder**: Location-based search with filtering by type (government/private/independent)
3. **Real-time Tracking**: Live ambulance location updates using Firebase Realtime Database
4. **First Aid Assistant**: AI-powered emergency guidance using Google Gemini API
5. **Hospital Locator**: Nearby hospital search with specialization filtering
6. **Driver Panel**: Interface for ambulance drivers to manage availability and requests

#### External Integrations
- **Google Maps API**: For location services, mapping, and route calculation
- **Firebase**: Real-time database for live tracking and authentication
- **Google Gemini AI**: For intelligent first aid recommendations
- **Geolocation API**: For automatic location detection

## Data Flow

### Emergency Request Flow
1. User initiates ambulance request through the finder interface
2. System queries available ambulances based on location and type
3. User selects ambulance and request is created in database
4. Driver receives notification and can accept/reject request
5. Real-time tracking begins once accepted
6. Status updates flow through Firebase for live synchronization

### Location Tracking
- Driver location updates pushed to Firebase Realtime Database
- Client subscribes to location changes for real-time map updates
- Route calculation performed using Google Maps Directions API
- ETA calculated and displayed to user

### AI First Aid Integration
- User describes emergency symptoms
- Request sent to Google Gemini API with emergency-specific prompt
- AI provides step-by-step first aid instructions
- Response formatted for emergency situations with safety warnings

## External Dependencies

### Core Dependencies
- **Database**: Drizzle ORM with PostgreSQL dialect
- **Authentication**: Firebase Auth (configured but not fully implemented)
- **Real-time Updates**: Firebase Realtime Database
- **Maps & Location**: Google Maps JavaScript API
- **AI**: Google Generative AI (Gemini)
- **UI Components**: Radix UI primitives
- **Validation**: Zod for schema validation

### Development Dependencies
- **TypeScript**: Type safety across frontend and backend
- **ESBuild**: Backend bundling for production
- **Vite Plugins**: Development enhancements including error overlay
- **Replit Integration**: Development environment optimizations

## Deployment Strategy

### Development Environment
- **Local Development**: Vite dev server with Express backend
- **Hot Reloading**: Vite middleware integration for seamless development
- **Environment Variables**: Separate configuration for API keys and database URLs

### Production Build
- **Frontend**: Vite build process generating static assets
- **Backend**: ESBuild bundling with external packages
- **Database**: Migration system using Drizzle Kit
- **Environment**: Node.js production server with static file serving

### Configuration Requirements
- `DATABASE_URL`: PostgreSQL connection string
- `VITE_GOOGLE_MAPS_API_KEY`: Google Maps API key
- `VITE_GEMINI_API_KEY`: Google Gemini API key
- `VITE_FIREBASE_*`: Firebase configuration variables

### Architectural Decisions

#### Database Choice
- **PostgreSQL with Drizzle**: Chosen for type safety, migration support, and scalability
- **Neon Database**: Serverless PostgreSQL for easy deployment and scaling
- **Schema Design**: Normalized structure with proper foreign key relationships

#### Real-time Communication
- **Firebase Realtime Database**: Selected for ambulance tracking due to real-time capabilities
- **REST API**: Used for standard CRUD operations with proper error handling
- **Hybrid Approach**: Combines REST for data management with Firebase for live updates

#### UI/UX Design
- **Emergency Color Scheme**: Red, blue, and white for immediate recognition
- **Mobile-First**: Responsive design prioritizing mobile emergency use cases
- **Component-Based**: Reusable components for ambulance and hospital cards
- **Accessibility**: ARIA labels and keyboard navigation support

#### Security Considerations
- **Input Validation**: Zod schemas for all API endpoints
- **Environment Variables**: Secure API key management
- **CORS**: Proper configuration for cross-origin requests
- **Error Handling**: Comprehensive error boundaries and logging

The architecture emphasizes rapid emergency response with real-time updates, intuitive user interface, and integration with essential external services for a comprehensive emergency assistance platform.