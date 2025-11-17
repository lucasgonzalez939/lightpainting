# Web Light Painting

A real-time light painting application that uses your webcam to create stunning long-exposure effects directly in your web browser.

## 🎨 Overview

This project allows you to create light painting effects using only your webcam and a web browser. Wave lights, glow sticks, or any bright object in front of your camera, and watch as beautiful trails are painted on your screen - just like long-exposure photography!

## ✨ Features

- **Real-time Light Painting**: Captures bright objects from your webcam and creates persistent light trails
- **Real-time Controls**: Adjust decay rate and brightness threshold on-the-fly with sliders
- **Adjustable Decay**: Light trails fade gradually over time for a natural long-exposure effect
- **Brightness Threshold**: Only captures objects above a certain brightness level
- **Live View Toggle**: Switch between seeing the live video feed or just the light painting
- **High Resolution Support**: Attempts to use 1080p resolution, with automatic fallback to 720p
- **Snapshot Capture**: Save your light painting as a PNG image
- **Video Recording**: Record your light painting session as a WebM video
- **Mirror Effect**: Video feed is horizontally flipped for intuitive interaction
- **Fullscreen Canvas**: Immersive full-screen painting experience

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Edge, or Safari)
- A working webcam
- Basic understanding of HTML (for customization)


## 🎮 Controls

The control panel at the bottom of the screen includes action buttons and real-time adjustment sliders:

### Action Buttons

- **Reiniciar Pintura** (Reset Painting): Clears the canvas and starts fresh
- **Ocultar/Mostrar Vista en Vivo** (Hide/Show Live View): Toggles the live webcam feed visibility
- **Capturar Instantánea** (Capture Snapshot): Downloads the current frame as a PNG image
- **Iniciar Grabación** (Start Recording): Begins recording your session
- **Detener Grabación** (Stop Recording): Stops recording and downloads the video

### Settings Sliders (Inline)

Adjust parameters in real-time:

- **Decay Slider**: Controls how fast light trails fade (0.80 - 0.99)
  - Lower values = faster fade, shorter trails
  - Higher values = slower fade, longer trails
- **Threshold Slider**: Controls minimum brightness to capture (10 - 100)
  - Lower values = captures dimmer lights
  - Higher values = only very bright sources

## 🔧 Configuration

The settings can be adjusted in real-time using the sliders in the bottom control panel, or you can set default values by modifying these parameters in the JavaScript section:

```javascript
// How fast the light fades (0.0 - 1.0)
// 1.0 = no fade, 0.95 = slow fade, 0.5 = fast fade
let DECAY_RATE = 0.95;

// Only pixels with brightness ABOVE this value will be painted
// Range: 0-255. Higher values = only very bright objects
let BRIGHTNESS_THRESHOLD = 30;

// Video resolution preferences
const VIDEO_CONSTRAINTS = {
    width: { ideal: 1920, max: 1920 },
    height: { ideal: 1080, max: 1080 }
};
```

### Parameter Guide

- **DECAY_RATE**: 
  - `0.99` - Very slow fade (long-lasting trails)
  - `0.95` - Moderate fade (default, balanced effect)
  - `0.90` - Faster fade (shorter trails)
  - `0.80` - Quick fade (brief trails)

- **BRIGHTNESS_THRESHOLD**:
  - `10` - Captures dimmer lights (more sensitive)
  - `30` - Default setting (balanced)
  - `50` - Only bright lights (LED flashlights, etc.)
  - `100` - Only very bright sources

## 🎯 How It Works

### Technical Architecture

The application uses three canvas layers:

1. **Composite Canvas** (visible): The final output shown to the user
2. **Live View Canvas** (hidden): Processes the current webcam frame
3. **Painting Canvas** (hidden): Accumulates the light trails with decay

### Rendering Pipeline

Each frame follows this process:

1. **Fade**: The painting canvas is drawn onto itself with reduced opacity (decay effect)
2. **Capture**: The current webcam frame is analyzed for brightness
3. **Threshold**: Pixels below the brightness threshold are made transparent
4. **Paint**: Bright pixels are added to the painting canvas using "lighter" blend mode
5. **Compose**: The live view (optional) and painting are combined on the visible canvas

### Key Technologies

- **Canvas API**: For image manipulation and rendering
- **WebRTC/getUserMedia**: For webcam access
- **MediaRecorder API**: For video recording
- **Tailwind CSS**: For UI styling
- **RequestAnimationFrame**: For smooth 60fps rendering

## 💡 Tips for Best Results

1. **Use bright light sources**: LED flashlights, glow sticks, or phone screens work great
2. **Work in a dark room**: Better contrast makes trails more visible
3. **Move slowly**: Smoother, more continuous trails
4. **Experiment with decay rates**: Find the perfect fade time for your style
5. **Try hiding the live view**: See only the light painting for a cleaner look
6. **Adjust brightness threshold**: Fine-tune what gets captured

## 🎨 Creative Ideas

- **Light writing**: Write words or draw pictures in the air
- **Abstract patterns**: Create swirling, flowing designs
- **Multiple lights**: Use different colored lights simultaneously
- **Collaborative art**: Multiple people painting with light together
- **Time-lapse effects**: Record and speed up your creation process

## 🔒 Privacy & Permissions

This application:
- ✅ Runs entirely in your browser (no server required)
- ✅ Does not upload any video or images
- ✅ Processes all data locally on your device
- ✅ Only requests webcam access (no audio)
- ✅ You can revoke camera permissions at any time


## 🛠️ Development

### Modifying the Code

The entire application is contained in a single HTML file for simplicity. To modify:

1. Open `index.html` in your text editor
2. The CSS is in the `<style>` section
3. The JavaScript is in the `<script>` section
4. The HTML structure is in the `<body>` section

### Extending Functionality

Ideas for enhancements:

- Add color filters or effects
- Implement brush size controls
- Save/load painting sessions
- Add music visualization
- Support multiple camera inputs
- Add preset effect configurations
- Implement undo/redo functionality

## 🐛 Troubleshooting

### Camera Not Starting

- **Check permissions**: Ensure you granted webcam access
- **Try HTTPS**: Some browsers require secure connection
- **Close other apps**: Other programs may be using your camera
- **Refresh the page**: Sometimes a simple refresh helps

### Low Performance

- **Lower resolution**: Modify `VIDEO_CONSTRAINTS` to use 720p
- **Close other tabs**: Free up system resources
- **Use Chrome**: Often has best canvas performance

### Black Screen

- **Check lighting**: Make sure there are bright objects to capture
- **Lower threshold**: Reduce `BRIGHTNESS_THRESHOLD` value
- **Reset painting**: Click the reset button to clear the canvas

## 📄 License

This project is open source and available for personal and educational use. Feel free to modify and share!

## 🤝 Contributing

Contributions are welcome! Some ways to contribute:

- Report bugs or issues
- Suggest new features
- Improve documentation
- Optimize performance
- Add example presets

## 📧 Support

For questions or issues:
1. Check the Troubleshooting section
2. Review the Configuration options
3. Open an issue on the repository

## 🎉 Acknowledgments

Inspired by long-exposure photography and the creative possibilities of web technologies.

---

**Made with ❤️ using vanilla JavaScript, Canvas API, and WebRTC**

*Create art with light, right in your browser!*
