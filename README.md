# 🏍️ Motorcycle Fuel Tracker • RPM Edition v2.0.2

**Experimental motorcycle fuel consumption tracker using GPS + Audio RPM detection**

## 🔧 Features

### **Engine RPM Detection**
- **Audio FFT Analysis**: Uses microphone to detect engine RPM from sound
- **Harmonic Analysis**: Analyzes 1st, 2nd, 3rd, and 4th harmonics
- **Multi-Cylinder Support**: Configurable for single, twin, triple, and quad cylinder engines
- **V-Twin Optimized**: Tuned for V-Twin engines like Victory and Harley-Davidson

### **Fuel Consumption Modeling**
- **RPM + Speed Integration**: Far more accurate than GPS-only tracking
- **Load-Aware Calculations**: Detects gear changes, hills, and acceleration via RPM analysis  
- **Engine Efficiency Curves**: Models real motorcycle engine performance characteristics
- **Smart Idle Detection**: Configurable idle consumption rates (gallons/hour)

### **PWA Implementation**
- **iOS/Android Compatible**: Full PWA support with offline capability
- **Real-Time Dashboard**: Speed, RPM, MPG, fuel used, range, trip distance
- **Pause/Resume Functionality**: Stop tracking when engine is off
- **Persistent Settings**: All calibration data saved locally

## 🔧 Current Status: v2.0.2

### **Proven Compatibility**
✅ **iOS Safari PWA** - Full microphone and GPS access confirmed  
✅ **Chrome Mobile** - Excellent performance and stability  
✅ **Victory V-Twin** - Optimized for 4th harmonic detection  
✅ **Multi-Cylinder Support** - 1-4 cylinder engine configurations  

### **Recent Improvements**
- **Fixed ambient noise false positives** (no more phantom RPM readings)
- **Enhanced V-Twin detection** with 4th harmonic prioritization
- **Improved signal smoothing** for stable idle readings
- **Professional noise rejection** algorithms
- **Confidence-based peak selection** for maximum accuracy

### **Testing Results**
- **Microphone access**: ✅ Works in iOS PWA standalone mode
- **GPS tracking**: ✅ Seamless integration with RPM detection  
- **Idle detection**: ✅ Correctly distinguishes ambient vs engine noise
- **Frequency analysis**: ✅ Accurate harmonic detection (tested at 70Hz)

## 🎯 Technical Implementation

### **Smart Acoustic Analysis**
- **FFT Size**: 2048 samples at 22050Hz for optimal frequency resolution
- **Update Rate**: 15fps for battery efficiency while maintaining responsiveness
- **Signal Processing**: Multi-peak detection with local maximum validation
- **Noise Rejection**: 120+ amplitude threshold with engine range validation

### **Fuel Consumption Algorithm**
- **Statistical Model**: Proven MPG-based calculations with RPM enhancements
- **Load Factor Analysis**: RPM vs expected RPM for speed detection
- **Efficiency Curves**: Engine RPM efficiency modeling (25-40% redline optimal)
- **Graceful Fallback**: Works with GPS-only when RPM unavailable

### **Engine Configuration**
- **Cylinder Count**: 1-4 cylinder support with harmonic calculations
- **RPM Range**: Configurable idle (600-2000) and redline (6000-15000)
- **Enable/Disable**: Optional RPM detection for compatibility
- **Calibration**: Highway/City MPG + Idle consumption + Engine specs

## 🧪 Experimental Status

This is an **experimental fuel tracking system** exploring the feasibility of audio-based RPM detection for motorcycles. The combination of GPS positioning and acoustic analysis aims to improve fuel consumption accuracy beyond GPS-only methods.

**Perfect for riders who want to:**
- Track real fuel efficiency across different riding conditions
- Understand how gear changes and riding style affect consumption  
- Monitor engine performance through RPM analysis
- Optimize routes and riding habits for maximum efficiency

## 🔬 Future Development

The foundation is solid for advanced features like:
- Automatic gear detection algorithms
- Route optimization with fuel efficiency mapping
- Engine health monitoring via acoustic analysis
- Integration with motorcycle maintenance schedules

---

**Built with web technologies and audio signal processing for motorcycle fuel analysis.** 🛣️

*v2.0.2 • RPM Edition - Experimental motorcycle fuel tracking with audio RPM detection*