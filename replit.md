# Mujassamat 3D Printing Services

## Overview

Mujassamat is a modern e-commerce platform for professional 3D printing services based in Jordan. The application provides a comprehensive quote system for customers to upload 3D files, specify printing requirements, and receive professional printing services. Built with a dark theme and focused on user experience, the platform serves as a bridge between customers and 3D printing services with features like multi-step quote forms, real-time 3D file previews, project galleries, and administrative tools for submission management.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The client-side application uses **React 18 with TypeScript** and **Wouter** for client-side routing instead of Next.js App Router. The UI is built with **Shadcn/UI components** and **Tailwind CSS** with a custom dark theme featuring blue/purple/cyan gradient accents. **Framer Motion** provides smooth animations throughout the interface, while **TanStack Query** handles all API interactions and state management. The application includes a comprehensive multi-step quote form with **React Hook Form** and **Zod validation**, plus **Three.js integration** for live STL file previews.

### Backend Architecture
The server runs on **Express.js with TypeScript** and uses **Multer** for handling file uploads up to 50MB. Currently implements an **in-memory storage system** through a custom `IStorage` interface, allowing for easy migration to database persistence later. The API includes rate limiting, comprehensive error handling, and RESTful endpoints for quotes, contact forms, and admin functionality. Email notifications are handled through a flexible system supporting multiple providers (mailto, EmailJS, Nodemailer).

### Data Management
Currently uses **file system storage** for uploaded files and **in-memory storage** for submission data, with plans for PostgreSQL integration via **Drizzle ORM**. The schema is already defined and ready for database migration. Submissions include comprehensive project details, material specifications, finishing options, and delivery preferences. File uploads support STL and OBJ formats with client-side validation.

### Authentication & Admin System
Implements a simple **admin key-based authentication** system for accessing submission management features. Admin users can view all submissions, update statuses, and manage the overall workflow. The system is designed to be easily upgraded to a full user authentication system when needed.

### UI/UX Design System
Features a **modern dark theme** with carefully crafted color variables and a glassmorphism aesthetic. The design system includes custom CSS classes for gradients, animations, and responsive layouts. Typography uses Inter font family with clear hierarchy, and the interface maintains AA contrast standards for accessibility.

## External Dependencies

### Core Framework Dependencies
- **React 18** with TypeScript for component architecture
- **Wouter** for lightweight client-side routing
- **Express.js** with TypeScript for server-side API
- **Vite** for development and build tooling

### UI & Styling
- **Tailwind CSS** for utility-first styling with custom dark theme
- **Shadcn/UI** component library with Radix UI primitives
- **Framer Motion** for animations and micro-interactions
- **Three.js** for 3D file preview functionality

### Data & Forms
- **TanStack Query** for server state management and API caching
- **React Hook Form** with **Zod** for form validation and type safety
- **Drizzle ORM** with PostgreSQL support (configured but not yet active)

### File Handling & Email
- **Multer** for multipart file upload handling
- **Nodemailer** for email functionality (configurable)
- Support for STL and OBJ file formats with size limits

### Development & Deployment
- **Replit** development environment with custom plugins
- **ESBuild** for production server bundling
- Custom build pipeline supporting both client and server TypeScript compilation

### Future Database Integration
The application is configured for **PostgreSQL** via **Neon Database** but currently uses in-memory storage. The database schema is defined and ready for migration when persistence is needed. Session management is prepared with **connect-pg-simple** for future authentication requirements.