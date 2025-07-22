# Adventure Box - Educational Activity Platform

## Overview

Adventure Box is a comprehensive full-stack educational platform designed to provide screen-free activities for children. The application helps parents and educators discover and manage 500+ educational activities using common household items, with features like progress tracking, badge systems, custom authentication, enterprise security, and subscription management with Stripe payment integration.

## User Preferences

Preferred communication style: Simple, everyday language.

## Recent Changes (Latest Updates)

### July 15, 2025
- **Database Enhancement**: Expanded activity database from 6 to 500+ activities across Science (150), Math (100), Physics (100), and Arts & Crafts (150)
- **Custom Authentication**: Replaced Replit auth with custom authentication system including password management, session handling, and security features
- **Security Features**: Added comprehensive security including 2FA, password change, email change, payment methods, saved addresses, and session management
- **Payment Integration**: Integrated Stripe payment processing for subscription management with support for major credit cards and digital wallets
- **Enterprise Security**: Added authentication tables for user passwords, sessions, 2FA, payment methods, addresses, and security logs
- **Settings Page**: Created comprehensive settings page with tabbed interface for profile, security, payments, addresses, and session management
- **CSS Fixes**: Resolved text visibility issues with improved color contrast and styling

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **UI Framework**: Radix UI components with shadcn/ui design system
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js server
- **Language**: TypeScript with ESM modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL store

### Key Components

#### Database Schema
- **Users**: Core user information with subscription management
- **Activities**: Educational activities with categorization, difficulty levels, and materials
- **Badges**: Achievement system with category-based requirements
- **User Progress**: Activity completion tracking with ratings and notes
- **User Badges**: Badge earning history
- **Sessions**: Authentication session storage

#### Authentication System
- Replit Auth integration with OpenID Connect
- Session-based authentication with PostgreSQL storage
- User profile management with subscription tiers (digital/premium)
- Protected routes with authentication middleware

#### Activity Management
- Categorized activities (science, math, physics, arts & crafts)
- Age-appropriate filtering (4-6, 7-12)
- Difficulty levels (easy, medium, hard)
- Material lists and instructions
- Premium content restrictions

#### Progress Tracking
- Activity completion with user ratings
- Personal notes and reflections
- Category-based statistics
- Achievement badges based on completion milestones

### Data Flow

1. **User Authentication**: 
   - Replit Auth handles OpenID Connect flow
   - Sessions stored in PostgreSQL with express-session
   - User data synchronized with local database

2. **Activity Discovery**:
   - Activities fetched with filtering options
   - Real-time search and categorization
   - Premium content access based on subscription

3. **Progress Management**:
   - Activity completion tracked with ratings
   - Badge system automatically awards achievements
   - Statistics calculated for user dashboard

4. **Admin Operations**:
   - CRUD operations for activities and badges
   - Content management with validation
   - Analytics and user management

### External Dependencies

#### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connection
- **drizzle-orm**: Type-safe database ORM
- **express**: Web server framework
- **react**: UI library
- **@tanstack/react-query**: Server state management
- **zod**: Runtime type validation
- **tailwindcss**: Utility-first CSS framework

#### Authentication
- **passport**: Authentication middleware
- **openid-client**: OpenID Connect implementation
- **express-session**: Session management
- **connect-pg-simple**: PostgreSQL session store

#### UI Components
- **@radix-ui/***: Headless UI components
- **lucide-react**: Icon library
- **react-hook-form**: Form handling
- **@hookform/resolvers**: Form validation integration

### Deployment Strategy

#### Development Environment
- **Local Development**: `npm run dev` starts both frontend and backend
- **Hot Reload**: Vite HMR for frontend, tsx for backend TypeScript execution
- **Database**: Drizzle Kit for schema migrations and management

#### Production Build
- **Frontend**: Vite builds optimized static assets
- **Backend**: esbuild bundles Node.js application
- **Database**: Drizzle migrations applied via `npm run db:push`
- **Environment**: Configured for Node.js production deployment

#### Key Architectural Decisions

1. **Monorepo Structure**: Single repository with shared TypeScript types between frontend and backend
2. **Database Choice**: PostgreSQL chosen for relational data with complex queries for progress tracking
3. **Authentication**: Replit Auth selected for seamless integration with deployment platform
4. **State Management**: TanStack Query for server state, avoiding complex client-side state management
5. **UI Framework**: Radix UI + shadcn/ui for accessible, customizable components
6. **Build Strategy**: Separate frontend/backend builds optimized for their respective environments

The application is designed to be scalable, maintainable, and user-friendly, with a focus on educational value and family engagement through screen-free activities.

## Complete System Architecture

### Frontend Architecture (React + TypeScript)
- **UI Framework**: React 18 with TypeScript for type safety
- **Build Tool**: Vite for fast development and optimized production builds
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **UI Components**: Radix UI with shadcn/ui design system for accessible components
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **Form Handling**: React Hook Form with Zod validation
- **Key Pages**: Landing, Home, Activities (500+ activities), Profile, Admin, Settings (comprehensive security)

### Backend Architecture (Node.js + Express)
- **Runtime**: Node.js with Express.js server
- **Language**: TypeScript with ESM modules
- **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Authentication**: Custom authentication system with session management
- **Payment Processing**: Stripe integration for subscription management
- **Security**: Password hashing, 2FA support, session management, security logging

### Database Schema Design
- **Core Tables**: 
  - `users` - User profiles with subscription tiers
  - `activities` - 500+ educational activities across 4 categories
  - `badges` - Achievement system with category-based requirements
  - `user_progress` - Activity completion tracking
  - `user_badges` - Badge earning history
  - `sessions` - Authentication session storage

- **Security Tables**:
  - `user_passwords` - Secure password storage with salt
  - `user_sessions` - Active session management
  - `user_two_factor` - 2FA authentication settings
  - `user_payment_methods` - Saved payment methods
  - `user_addresses` - Billing and shipping addresses
  - `user_security_logs` - Security audit trail

### Authentication & Security System
- **Custom Authentication**: Password-based login with session management
- **Session Security**: PostgreSQL session store with expiration
- **Two-Factor Authentication**: TOTP support with backup codes
- **Password Security**: Scrypt hashing with salt for password storage
- **Security Monitoring**: Comprehensive logging of all security events
- **Payment Security**: Stripe integration with PCI compliance

### Payment & Subscription System
- **Payment Processor**: Stripe integration with webhook support
- **Subscription Tiers**: 
  - Digital Plan ($39/month) - Basic activities access
  - Premium Plan ($99/month) - Full access + premium activities
- **Payment Methods**: Credit cards, Apple Pay, Google Pay support
- **Subscription Management**: Upgrade/downgrade, cancellation, billing history

### Activity Management System
- **Activity Categories**: Science (150), Math (100), Physics (100), Arts & Crafts (150)
- **Age Targeting**: Activities for ages 4-6 and 7-12
- **Difficulty Levels**: Easy, Medium, Hard progression
- **Material Lists**: Common household items for each activity
- **Premium Content**: Enhanced activities for premium subscribers
- **Progress Tracking**: User completion rates and ratings

### Badge & Achievement System
- **Category-Based Badges**: Rewards for completing activities in each category
- **Progress Tracking**: Real-time badge progress calculation
- **Achievement Milestones**: Badges for 5, 10, 25, 50 completed activities
- **Visual Feedback**: Progress bars and achievement notifications

### Enterprise Security Features
- **Profile Management**: First name, last name, email updates
- **Password Management**: Current password verification, secure password changes
- **Two-Factor Authentication**: Enable/disable 2FA with backup codes
- **Payment Methods**: Add/remove credit cards, set default payment method
- **Address Management**: Billing and shipping address storage
- **Session Management**: View active sessions, terminate sessions remotely
- **Security Audit**: Complete log of all security-related actions
- **Account Recovery**: Password reset and account recovery options

### API Architecture
- **RESTful Endpoints**: Standard HTTP methods for CRUD operations
- **Authentication Middleware**: Session-based authentication for protected routes
- **Data Validation**: Zod schema validation for all inputs
- **Error Handling**: Consistent error responses with proper HTTP status codes
- **Rate Limiting**: Protection against API abuse
- **CORS Configuration**: Secure cross-origin resource sharing

### Development & Deployment
- **Development Environment**: Hot module replacement with Vite
- **Database Migrations**: Drizzle Kit for schema management
- **Type Safety**: Shared TypeScript types between frontend and backend
- **Build Process**: Separate frontend and backend builds
- **Environment Configuration**: Environment variables for sensitive data
- **Production Deployment**: Optimized builds for production environment

### Technology Stack Summary
- **Frontend**: React 18, TypeScript, Vite, Wouter, TanStack Query, Radix UI, Tailwind CSS
- **Backend**: Node.js, Express.js, TypeScript, Drizzle ORM
- **Database**: PostgreSQL (Neon), session storage
- **Authentication**: Custom session-based auth with 2FA
- **Payment**: Stripe integration
- **Security**: Password hashing, session management, audit logging
- **Deployment**: Replit-optimized configuration

The platform successfully provides a comprehensive educational experience with enterprise-grade security, payment processing, and a rich activity database designed to engage children in screen-free learning.