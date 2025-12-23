# 🎆 Interactive 3D Particle System with Hand Gesture Control

A real-time 3D particle system controlled by hand gestures using your webcam. Built with Three.js and MediaPipe Hands AI.

![Project Demo](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![Technology](https://img.shields.io/badge/Tech-Three.js%20%7C%20MediaPipe-blue)
![License](https://img.shields.io/badge/License-Free%20to%20Use-orange)

## ✨ Features

- 🖐️ **Hand Gesture Control** - Move hands apart/together to expand/contract particles
- 🎨 **6 Particle Templates** - Heart, Flower, Saturn, Buddha, Fireworks, Sphere
- 🌈 **Color Customization** - Full color picker + 8 presets
- ⚡ **Real-time Tracking** - 60 FPS smooth animations
- 📱 **Responsive Design** - Works on desktop and mobile
- 🎯 **Zero Dependencies** - Single HTML file, no build process

## 🚀 Quick Start

### Option 1: Local (Instant)
1. Download `particle-system.html`
2. Open in any modern browser
3. Allow camera access
4. Show both hands and start controlling!

### Option 2: Web Deploy
Upload to any static hosting:
- GitHub Pages
- Netlify
- Vercel
- Your own server

⚠️ **Important:** HTTPS required for camera access in production

## 🎮 How to Use

### Gesture Controls
- **Expand:** Move both hands apart
- **Contract:** Bring both hands together
- **Reset:** Remove hands from view

### UI Controls
1. **Template Panel** - Click any template to change particle shape
2. **Color Picker** - Choose custom colors or use presets
3. **Camera Toggle** - Enable/disable hand tracking

## 🛠️ Technical Stack

- **Three.js r128** - 3D graphics rendering
- **MediaPipe Hands** - AI hand tracking
- **Vanilla JavaScript** - No frameworks
- **CSS3** - Modern UI with glassmorphism

## 📋 Requirements

- Modern browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Webcam access
- WebGL support
- HTTPS (for production deployment)

## 🎨 Templates

| Template | Particles | Description |
|----------|-----------|-------------|
| 💖 Heart | 2,000 | Parametric 3D heart |
| 🌸 Flower | 3,000 | 8-petal design |
| 🪐 Saturn | 2,500 | Planet with rings |
| 🧘 Buddha | 4,000 | Meditation pose |
| 🎆 Fireworks | 5,000 | Multiple bursts |
| ⚫ Sphere | 3,000 | Classic sphere |

## 📐 Particle Math Examples

### Heart Shape
```javascript
// Parametric heart equation
x = r * (16 * sin³(t))
y = r * (13cos(t) - 5cos(2t) - 2cos(3t) - cos(4t))
z = r * sin(u) * 3
```

### Flower Shape
```javascript
// Polar coordinates with petal function
r = radius * (1 + 0.5 * sin(8 * angle))
x = r * cos(angle)
y = r * sin(angle)
```

## 🎯 Key Features Explained

### Hand Tracking
- Detects up to 2 hands simultaneously
- Tracks 21 landmarks per hand
- Calculates 3D distance between hands
- Maps distance to particle scale (0.2x - 3.0x)

### Smooth Animations
- Easing function: `scale += (target - current) * 0.1`
- Continuous particle rotation
- 60 FPS targeting
- Responsive to window resize

### Performance Optimization
- BufferGeometry for efficient memory
- AdditiveBlending for GPU acceleration
- Point particles (not mesh)
- Minimal DOM manipulation

## 🔧 Customization

### Add New Template
```javascript
// 1. Create generation function
function generateCustomShape(count) {
    const positions = [];
    for (let i = 0; i < count; i++) {
        // Your math here
        positions.push(x, y, z);
    }
    return positions;
}

// 2. Add to switch statement
case 'custom':
    positions = generateCustomShape(3000);
    break;

// 3. Add UI button
<div class="template-btn" data-template="custom">
    <div class="template-icon">🎭</div>
    <div class="template-label">Custom</div>
</div>
```

### Adjust Performance
```javascript
// Lower particle count for slower devices
generateHeartShape(1000) // Instead of 2000

// Reduce quality for performance
renderer.setPixelRatio(1) // Instead of devicePixelRatio

// Simplify hand tracking
modelComplexity: 0 // Instead of 1
```

### Change Colors
```css
/* Update CSS variables */
:root {
    --primary: #00ffcc;    /* Cyan */
    --secondary: #ff006e;  /* Magenta */
    --accent: #8338ec;     /* Purple */
}
```

## 🐛 Troubleshooting

### Camera not working
- Ensure HTTPS in production
- Check browser permissions
- Verify camera not used by other app
- Try different browser

### Low performance
- Reduce particle count
- Lower pixel ratio
- Disable hand tracking temporarily
- Close other tabs

### Particles not visible
- Check camera position (z = 30)
- Verify particle size (0.15)
- Adjust fog density
- Check material opacity

## 📱 Browser Support

| Browser | Desktop | Mobile | Hand Tracking |
|---------|---------|--------|---------------|
| Chrome | ✅ 90+ | ✅ | ✅ |
| Firefox | ✅ 88+ | ✅ | ✅ |
| Safari | ✅ 14+ | ✅ | ✅ |
| Edge | ✅ 90+ | ✅ | ✅ |

## 📊 Performance Targets

- **FPS:** 60
- **Response Time:** <100ms
- **Memory:** <50MB
- **Load Size:** <5MB

## 📚 Documentation

See `PROJECT-GUIDE.md` for comprehensive documentation including:
- Detailed code explanations
- Mathematical formulas
- Architecture overview
- Advanced customization
- Learning resources

## 🚀 Deployment

### GitHub Pages
```bash
git init
git add .
git commit -m "Initial commit"
git push -u origin main
# Enable Pages in repo settings
```

### Netlify
1. Drag and drop HTML file
2. Get instant HTTPS URL

### Vercel
```bash
npm i -g vercel
vercel
```

## 🎓 Learning Resources

- [Three.js Documentation](https://threejs.org/docs/)
- [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands)
- [WebGL Fundamentals](https://webglfundamentals.org/)

## 🔮 Future Enhancements

- [ ] Recording & export animations
- [ ] Audio reactivity
- [ ] VR support with WebXR
- [ ] Advanced gestures (pinch, swipe)
- [ ] Particle physics simulation
- [ ] Custom template builder
- [ ] Multiplayer mode

## 📝 File Structure

```
project/
├── particle-system.html   # Main application (single file)
├── PROJECT-GUIDE.md       # Comprehensive documentation
└── README.md              # This file
```

## 💡 Tips & Tricks

1. **Better Tracking:** Use good lighting and plain background
2. **Smooth Gestures:** Move hands slowly for better response
3. **Color Combos:** Try complementary colors for striking effects
4. **Template Mixing:** Switch templates while gesturing for transitions
5. **Performance:** Disable tracking when not actively using gestures

## 🎨 Design Philosophy

- **Cyberpunk Aesthetic** - Neon colors, dark background, glowing effects
- **Minimal UI** - Control panel with glassmorphism
- **Smooth Interactions** - Easing functions for natural feel
- **Responsive** - Works on all screen sizes
- **Accessible** - Clear visual feedback and status indicators

## 🌟 Highlights

✅ **Zero Build Process** - Just open and run  
✅ **Self-Contained** - All code in one file  
✅ **Production Ready** - Optimized and tested  
✅ **Well Documented** - Comprehensive guides  
✅ **Easily Customizable** - Modular architecture  
✅ **Educational** - Great for learning 3D graphics  

## 📧 Questions?

Check `PROJECT-GUIDE.md` for detailed explanations, troubleshooting, and advanced topics.

---

**Built with ❤️ using Three.js, MediaPipe, and modern web technologies**

*Free to use, modify, and distribute. No attribution required but appreciated!*

---

### Quick Links
- 📖 [Full Documentation](PROJECT-GUIDE.md)
- 🎨 [Three.js Docs](https://threejs.org/docs/)
- 🖐️ [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands)

### Stats
⭐ Features: 6 templates, gesture control, color customization  
📦 Size: ~30KB (single HTML file)  
⚡ Performance: 60 FPS target  
🌐 Compatibility: All modern browsers  

**Ready to create amazing particle effects with your hands? Let's go! 🚀**
