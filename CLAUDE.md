# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file Progressive Web App (PWA) that estimates motorcycle fuel consumption using GPS speed data with comprehensive cornering analytics and automated versioning. The entire application is contained in `index.html` with inline CSS, JavaScript, and PWA manifest.

## Architecture

**Single-File Structure**: The application uses a self-contained approach with:
- Embedded PWA manifest and service worker (base64 encoded in HTML)
- Inline CSS with responsive design and glassmorphic styling
- Vanilla JavaScript with GPS geolocation API integration
- Local storage for data persistence
- Automated version injection via GitHub Actions

**Core Components**:
- GPS tracking with position interpolation and speed calculation
- Fuel consumption estimation using configurable speed/MPG calibration points
- **Cornering Analytics**: Aircraft-style artificial horizon for roll angle display
- **Lateral G-Force**: Real-time sideways acceleration measurement
- **Remaining Daylight**: GPS-based sunset calculation for ride planning
- Audio-based RPM detection with gear shift detection
- Comprehensive data logging with CSV export (38+ telemetry fields)
- PWA capabilities (offline support, installable, wake lock)

**Key Technical Details**:
- Uses Haversine formula for GPS distance calculations
- Implements linear interpolation between highway/city MPG calibration points
- **Enhanced GPS filtering**: 20m accuracy threshold, speed validation
- **Roll angle calculation**: Median filtering, 3° deadband, steady-state detection
- **RPM detection**: Audio FFT analysis with adaptive thresholds during gear shifts
- **Astronomical calculations**: Solar declination for precise sunset timing
- Persists state in localStorage with automatic save/restore

## Development & Deployment

**Automated Versioning**: Uses GitHub Actions for version injection:
- Version placeholders (`{{VERSION}}`, `{{BUILD_DATE}}`) in HTML
- Tag-based releases (v2.5.3) trigger production deployments
- Main branch pushes create development builds (dev-{hash})
- Deploys to `gh-pages` branch to bypass environment protection rules

**Testing**: Open `index.html` in a browser. For PWA features and GPS testing, serve over HTTPS (required for geolocation and service worker).

**Release Workflow**:
```bash
git tag v2.6.0
git push origin v2.6.0  # Triggers automated deployment
```

See `DEPLOYMENT.md` for complete deployment documentation.

## Key Implementation Notes

- GPS permission is required on first use
- Application designed for mobile with touch-optimized controls
- Service worker and manifest are inline for single-file deployment
- Tank capacity defaults to 4.5 gallons (motorcycle-specific)
- **Idle RPM calibrated to 950** (motorcycle-specific, not car default)
- **Roll angle filtering**: Uses Y-axis for motorcycle lean angle, only calculates during steady-state (8-12 m/s² total acceleration)
- **Audio RPM thresholds**: Adaptive based on gear shift detection (160-220 amplitude)
- **Color-coded severity**: Green/Yellow/Orange/Red for lean angles and G-forces
- Wake lock prevents screen sleep during tracking

## Recent Major Features (v2.4.0+)

- **v2.4.0**: Cornering analytics with roll angle artificial horizon
- **v2.5.0**: Remaining daylight calculator for ride planning
- **v2.5.x**: Automated version injection and deployment system
- **Ongoing**: Enhanced RPM detection accuracy and gear shift awareness

## EXPERIMENTAL DEVELOPMENT STATUS (September 2025)

**⚠️ CURRENT BRANCH: Experimental Accelerometer RPM Detection**

This branch contains significant experimental changes that may need rollback:

### **Major Additions**:
- **Dual RPM Detection System**: Added accelerometer-based RPM backup using Z-axis vibration FFT analysis
- **Signal Amplification**: 2.5x amplification factor for weak accelerometer signals
- **Ultra-Sensitive Thresholds**: Reduced amplitude threshold from 0.01 to 0.003 (experimental)
- **10Hz Data Logging**: Increased from GPS-triggered to 100ms timer-based logging
- **UI Consolidation**: Removed JSON export, consolidated fuel displays, simplified interface

### **Validation Results**:
- **CSV Data Analysis Confirmed**: Real correlation between audio and accelerometer RPM
  - Example readings: Audio=191/Accel=186, Audio=192/Accel=190
- **Roll Indicator**: Fixed responsiveness issues with proper gravity isolation
- **Performance**: Higher frequency logging working without stability issues

### **Rollback Considerations**:
- If accelerometer RPM proves unstable or battery-draining, revert to audio-only
- 10Hz logging may impact battery life on longer rides
- Ultra-sensitive thresholds might introduce false positives
- Current implementation is highly experimental and needs extensive field testing

### **Testing Environment**:
- Always remember this is a mobile web app. Console debugging is not available
- The motorcycle under test is a 2012 Victory Highball, and an iPhone 13 mounted on the handlebar
- Remember that this cannot be tested locally - requires mobile deployment for sensor access