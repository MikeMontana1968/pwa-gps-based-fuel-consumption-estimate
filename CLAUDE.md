# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file Progressive Web App (PWA) that estimates motorcycle fuel consumption using GPS speed data. The entire application is contained in `index.html` with inline CSS, JavaScript, and PWA manifest.

## Architecture

**Single-File Structure**: The application uses a self-contained approach with:
- Embedded PWA manifest and service worker (base64 encoded in HTML)
- Inline CSS with responsive design and glassmorphic styling
- Vanilla JavaScript with GPS geolocation API integration
- Local storage for data persistence

**Core Components**:
- GPS tracking with position interpolation and speed calculation
- Fuel consumption estimation using configurable speed/MPG calibration points
- Real-time metrics display (speed, MPG, fuel used, range, trip distance)
- PWA capabilities (offline support, installable, wake lock)

**Key Technical Details**:
- Uses Haversine formula for GPS distance calculations
- Implements linear interpolation between highway/city MPG calibration points
- Filters GPS noise with accuracy and speed thresholds
- Persists state in localStorage with automatic save/restore

## Development

**No Build Process**: This is a static HTML file that can be opened directly in a browser or served by any web server.

**Testing**: Open `index.html` in a browser. For PWA features and GPS testing, serve over HTTPS (required for geolocation and service worker).

**Deployment**: Copy the single `index.html` file to any web server. No build, compile, or dependency installation required.

## Key Implementation Notes

- GPS permission is required on first use
- Application designed for mobile with touch-optimized controls
- Service worker and manifest are inline for single-file deployment
- Tank capacity defaults to 4.5 gallons (motorcycle-specific)
- MPG interpolation handles edge cases (idle, high speed extrapolation)
- Wake lock prevents screen sleep during tracking