# Flutter Route Shifter

A powerful, declarative route transition package with chainable animations, shared elements, and advanced effects for Flutter applications.

[![pub package](https://img.shields.io/pub/v/flutter_route_shifter.svg)](https://pub.dev/packages/flutter_route_shifter)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Flutter](https://img.shields.io/badge/Flutter-3.7%2B-blue.svg)](https://flutter.dev/)
[![Dart](https://img.shields.io/badge/Dart-3.1%2B-blue.svg)](https://dart.dev/)

## ✨ Features

- **🔗 Chainable API**: Intuitive `.fade().slide().scale()` syntax for combining effects
- **🎨 Rich Effects**: 50+ built-in animation effects including fade, slide, scale, rotation, blur, shear, and more
- **🚀 Shared Elements**: Hero-like transitions between pages with advanced shared element support
- **📱 Platform Presets**: Material Design and Cupertino (iOS) style transitions
- **👆 Interactive Dismiss**: Swipe-to-dismiss gestures with customizable directions
- **⏱️ Staggered Animations**: Beautiful cascading effects for lists and grids
- **🎯 Performance Optimized**: Efficient animations with minimal overhead
- **🛠️ Highly Customizable**: Custom curves, durations, and timing controls
- **🎪 Creative Effects**: Follow-path animations, parallax effects, clip-path transitions
- **📐 Advanced Geometry**: Shear, perspective, and 3D-like transformations
- **🎨 Color Effects**: Tint and color transition animations
- **🧩 Modular Architecture**: Clean, maintainable codebase with mixin-based structure

## 🚀 Getting Started

### Installation

Add this to your package's `pubspec.yaml` file:

```yaml
dependencies:
  flutter_route_shifter: ^1.0.0
```

Then run:

```bash
$ flutter pub get
```

### Basic Usage

```dart
import 'package:flutter_route_shifter/flutter_route_shifter.dart';

// Simple fade transition
final route = RouteShifterBuilder()
  .fade(duration: Duration(milliseconds: 300))
  .toRoute(page: NextPage());

Navigator.of(context).push(route);
```

## 🎨 Complete Effects Guide

### Core Animation Effects

#### Fade Transitions
```dart
// Basic fade
RouteShifterBuilder()
  .fade(
    duration: Duration(milliseconds: 400),
    curve: Curves.easeInOut,
  )

// Fade with opacity control
RouteShifterBuilder()
  .fade(
    beginOpacity: 0.0,
    endOpacity: 1.0,
    duration: Duration(milliseconds: 500),
  )

// Fade with intervals (for staggered effects)
RouteShifterBuilder()
  .fade(
    duration: Duration(milliseconds: 600),
    intervalStart: 0.2,
    intervalEnd: 0.8,
  )
```

#### Slide Transitions
```dart
// Slide from right
RouteShifterBuilder()
  .slide(
    beginOffset: Offset(1.0, 0.0),
    endOffset: Offset.zero,
    duration: Duration(milliseconds: 300),
  )

// Slide from bottom
RouteShifterBuilder()
  .slide(
    beginOffset: Offset(0.0, 1.0),
    curve: Curves.easeOutCubic,
  )

// Slide with custom curve
RouteShifterBuilder()
  .slide(
    beginOffset: Offset(-1.0, 0.0),
    curve: Curves.elasticOut,
    duration: Duration(milliseconds: 800),
  )
```

#### Scale Transitions
```dart
// Scale from center
RouteShifterBuilder()
  .scale(
    beginScale: 0.0,
    endScale: 1.0,
    duration: Duration(milliseconds: 400),
  )

// Scale with alignment
RouteShifterBuilder()
  .scale(
    beginScale: 0.8,
    alignment: Alignment.bottomRight,
    curve: Curves.bounceOut,
  )

// Non-uniform scaling
RouteShifterBuilder()
  .scale(
    beginScale: 0.5,
    endScale: 1.2,
    duration: Duration(milliseconds: 500),
  )
```

#### Rotation Transitions
```dart
// Simple rotation
RouteShifterBuilder()
  .rotation(
    beginAngle: 0.0,
    endAngle: math.pi * 2,
    duration: Duration(milliseconds: 600),
  )

// Rotation with alignment
RouteShifterBuilder()
  .rotation(
    beginAngle: -math.pi / 4,
    endAngle: 0.0,
    alignment: Alignment.topLeft,
  )

// Quarter turn rotation
RouteShifterBuilder()
  .rotation(
    beginAngle: math.pi / 2,
    curve: Curves.easeInOutBack,
  )
```

### Advanced Visual Effects

#### Blur Effects
```dart
// Gaussian blur
RouteShifterBuilder()
  .blur(
    beginBlur: 0.0,
    endBlur: 10.0,
    duration: Duration(milliseconds: 400),
  )

// Motion blur effect
RouteShifterBuilder()
  .blur(
    beginBlur: 5.0,
    endBlur: 0.0,
    curve: Curves.easeOut,
  )
```

#### Shear Transformations
```dart
// Horizontal shear
RouteShifterBuilder()
  .shear(
    beginShear: Offset(0.0, 0.0),
    endShear: Offset(0.2, 0.0),
    duration: Duration(milliseconds: 500),
  )

// Vertical shear
RouteShifterBuilder()
  .shear(
    beginShear: Offset(0.0, 0.3),
    endShear: Offset.zero,
  )
```

#### Color Tint Effects
```dart
// Color overlay
RouteShifterBuilder()
  .tint(
    beginColor: Colors.blue.withOpacity(0.0),
    endColor: Colors.blue.withOpacity(0.3),
    blendMode: BlendMode.overlay,
  )

// Color transition
RouteShifterBuilder()
  .tint(
    beginColor: Colors.red,
    endColor: Colors.transparent,
    duration: Duration(milliseconds: 400),
  )
```

### Creative and Complex Effects

#### Flip Transitions
```dart
// Horizontal flip
RouteShifterBuilder()
  .flip(
    axis: FlipAxis.horizontal,
    duration: Duration(milliseconds: 600),
    perspective: 0.001,
  )

// Vertical flip
RouteShifterBuilder()
  .flip(
    axis: FlipAxis.vertical,
    curve: Curves.easeInOutCubic,
  )
```

#### Ripple Effects
```dart
// Ripple from center
RouteShifterBuilder()
  .ripple(
    center: Offset(0.5, 0.5),
    radius: 1.0,
    duration: Duration(milliseconds: 800),
  )

// Custom ripple
RouteShifterBuilder()
  .ripple(
    center: Offset(0.0, 1.0), // Bottom-left
    beginRadius: 0.0,
    endRadius: 1.5,
  )
```

#### Morph Transitions
```dart
// Shape morphing
RouteShifterBuilder()
  .morph(
    beginPath: circlePath,
    endPath: squarePath,
    duration: Duration(milliseconds: 700),
  )
```

### Staggered Animations

```dart
// List stagger effect
RouteShifterBuilder()
  .stagger(
    effects: [
      StaggerEffect.fade(delay: Duration(milliseconds: 50)),
      StaggerEffect.slide(
        beginOffset: Offset(0, 0.2),
        delay: Duration(milliseconds: 100),
      ),
    ],
    itemCount: 10,
    duration: Duration(milliseconds: 800),
  )

// Grid stagger
RouteShifterBuilder()
  .stagger(
    effects: [
      StaggerEffect.scale(beginScale: 0.8),
      StaggerEffect.fade(),
    ],
    staggerDirection: StaggerDirection.topLeftToBottomRight,
    itemCount: 20,
  )
```

## 🔗 Chaining Effects

One of the most powerful features is the ability to chain multiple effects:

```dart
// Complex transition combining multiple effects
final route = RouteShifterBuilder()
  .fade(
    duration: Duration(milliseconds: 400),
    intervalStart: 0.0,
    intervalEnd: 0.7,
  )
  .slide(
    beginOffset: Offset(1.0, 0.0),
    duration: Duration(milliseconds: 500),
    curve: Curves.easeOutCubic,
  )
  .scale(
    beginScale: 0.8,
    duration: Duration(milliseconds: 600),
    curve: Curves.elasticOut,
  )
  .rotation(
    beginAngle: math.pi / 8,
    endAngle: 0.0,
    duration: Duration(milliseconds: 400),
  )
  .toRoute(page: NextPage());

Navigator.of(context).push(route);
```

## 🚀 Shared Element Transitions

### Basic Shared Elements

```dart
// Source page - wrap elements in Shifter widgets
Shifter(
  shiftId: 'hero-image',
  child: Container(
    width: 100,
    height: 100,
    child: Image.asset('assets/image.jpg'),
  ),
)

// Target page - use same shiftId
Shifter(
  shiftId: 'hero-image',
  child: Container(
    width: 300,
    height: 200,
    child: Image.asset('assets/image.jpg'),
  ),
)

// Navigation with shared elements
final route = RouteShifterBuilder()
  .sharedElements(
    flightDuration: Duration(milliseconds: 600),
    flightCurve: Curves.easeInOutCubic,
    enableMorphing: true,
    useElevation: true,
  )
  .toRoute(page: DetailPage());
```

### Advanced Shared Elements

```dart
// Multiple shared elements
final route = RouteShifterBuilder()
  .sharedElements(
    flightDuration: Duration(milliseconds: 800),
    flightCurve: Curves.easeInOutBack,
    enableMorphing: true,
    useElevation: true,
    shiftIds: ['hero-image', 'hero-title', 'hero-subtitle'],
  )
  .fade(
    duration: Duration(milliseconds: 400),
    intervalStart: 0.3,
    intervalEnd: 1.0,
  )
  .toRoute(page: DetailPage());
```

### Shared Element Configuration

```dart
RouteShifterBuilder()
  .sharedElements(
    // Flight animation duration
    flightDuration: Duration(milliseconds: 600),
    
    // Flight path curve
    flightCurve: Curves.easeInOutCubic,
    
    // Enable shape morphing
    enableMorphing: true,
    
    // Add elevation during flight
    useElevation: true,
    
    // Custom elevation value
    flightElevation: 8.0,
    
    // Specific elements to animate
    shiftIds: ['image', 'title'],
    
    // Morphing curve (if different from flight curve)
    morphCurve: Curves.easeInOut,
  )
```

## 📱 Platform-Specific Presets

### Material Design Transitions

```dart
// Material slide up
RouteShifterBuilder()
  .materialSlideUp()
  .toRoute(page: NextPage());

// Material fade through
RouteShifterBuilder()
  .materialFadeThrough()
  .toRoute(page: NextPage());

// Material shared axis
RouteShifterBuilder()
  .materialSharedAxis(
    axis: SharedAxisDirection.horizontal,
  )
  .toRoute(page: NextPage());

// Material container transform
RouteShifterBuilder()
  .materialContainerTransform()
  .sharedElements()
  .toRoute(page: NextPage());
```

### Cupertino (iOS) Transitions

```dart
// iOS-style slide
RouteShifterBuilder()
  .cupertinoSlide()
  .toRoute(page: NextPage());

// iOS modal presentation
RouteShifterBuilder()
  .cupertinoModal()
  .toRoute(page: NextPage());

// iOS page transition
RouteShifterBuilder()
  .cupertinoPageTransition()
  .toRoute(page: NextPage());
```

## 👆 Interactive Gestures

### Swipe to Dismiss

```dart
// Enable swipe down to dismiss
RouteShifterBuilder()
  .fade(duration: Duration(milliseconds: 300))
  .enableInteractiveDismiss(
    direction: DismissDirection.down,
  )
  .toRoute(page: NextPage());

// Multiple dismiss directions
RouteShifterBuilder()
  .slide(beginOffset: Offset(0, 1))
  .enableInteractiveDismiss(
    direction: DismissDirection.vertical,
  )
  .toRoute(page: NextPage());

// Custom dismiss threshold
RouteShifterBuilder()
  .scale(beginScale: 0.9)
  .enableInteractiveDismiss(
    direction: DismissDirection.horizontal,
    dismissThreshold: 0.3,
  )
  .toRoute(page: NextPage());
```

## ⚙️ Advanced Configuration

### Custom Curves

```dart
// Using built-in curves
RouteShifterBuilder()
  .fade(curve: Curves.bounceOut)
  .slide(curve: Curves.elasticInOut)
  .scale(curve: Curves.backInOut)
  .toRoute(page: NextPage());

// Custom cubic curve
final customCurve = Cubic(0.25, 0.1, 0.25, 1.0);
RouteShifterBuilder()
  .fade(curve: customCurve)
  .toRoute(page: NextPage());

// Stepped curve
RouteShifterBuilder()
  .slide(curve: Curves.fastLinearToSlowEaseIn)
  .toRoute(page: NextPage());
```

### Duration Extensions

```dart
// Using duration extensions for cleaner code
RouteShifterBuilder()
  .fade(duration: 300.ms)
  .slide(duration: 0.5.seconds)
  .scale(duration: 1.2.seconds)
  .toRoute(page: NextPage());
```

### Timing Control

```dart
// Interval control for overlapping animations
RouteShifterBuilder()
  .fade(
    duration: 1.seconds,
    intervalStart: 0.0,
    intervalEnd: 0.6,
  )
  .slide(
    duration: 1.seconds,
    intervalStart: 0.2,
    intervalEnd: 1.0,
  )
  .toRoute(page: NextPage());
```

## 🎯 Performance Tips

### Optimizing Animations

```dart
// Use appropriate durations
RouteShifterBuilder()
  .fade(duration: 250.ms)      // Fast for simple transitions
  .slide(duration: 300.ms)     // Standard for slide
  .scale(duration: 400.ms)     // Slightly slower for scale
  .toRoute(page: NextPage());

// Avoid too many concurrent effects
RouteShifterBuilder()
  .fade()
  .slide()
  // Don't add too many more effects
  .toRoute(page: NextPage());
```

### Memory Management

```dart
// Dispose controllers properly (automatic)
// The package handles controller disposal automatically

// Use const constructors when possible
const NextPage()  // Better than NextPage()
```

## 📋 Complete Example

Here's a comprehensive example showing multiple features:

```dart
import 'package:flutter/material.dart';
import 'package:flutter_route_shifter/flutter_route_shifter.dart';

class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Route Shifter Demo')),
      body: ListView(
        children: [
          // Shared element example
          Shifter(
            shiftId: 'hero-card',
            child: Card(
              child: ListTile(
                leading: Shifter(
                  shiftId: 'hero-avatar',
                  child: CircleAvatar(
                    backgroundImage: AssetImage('assets/avatar.jpg'),
                  ),
                ),
                title: Shifter(
                  shiftId: 'hero-title',
                  child: Text('John Doe'),
                ),
                subtitle: Text('Tap to view profile'),
                onTap: () => _navigateToProfile(context),
              ),
            ),
          ),
          
          // Regular transition examples
          _buildTransitionButton(
            context,
            'Fade Transition',
            () => _navigateWithFade(context),
          ),
          _buildTransitionButton(
            context,
            'Complex Transition',
            () => _navigateWithComplexTransition(context),
          ),
        ],
      ),
    );
  }

  void _navigateToProfile(BuildContext context) {
    final route = RouteShifterBuilder()
      .sharedElements(
        flightDuration: Duration(milliseconds: 600),
        enableMorphing: true,
        shiftIds: ['hero-card', 'hero-avatar', 'hero-title'],
      )
      .fade(
        duration: Duration(milliseconds: 400),
        intervalStart: 0.3,
        intervalEnd: 1.0,
      )
      .toRoute(page: ProfilePage());
    
    Navigator.of(context).push(route);
  }

  void _navigateWithFade(BuildContext context) {
    final route = RouteShifterBuilder()
      .fade(duration: 300.ms)
      .toRoute(page: NextPage());
    
    Navigator.of(context).push(route);
  }

  void _navigateWithComplexTransition(BuildContext context) {
    final route = RouteShifterBuilder()
      .fade(duration: 400.ms, intervalStart: 0.0, intervalEnd: 0.7)
      .slide(
        beginOffset: Offset(1.0, 0.0),
        duration: 500.ms,
        curve: Curves.easeOutCubic,
      )
      .scale(
        beginScale: 0.8,
        duration: 600.ms,
        curve: Curves.elasticOut,
      )
      .enableInteractiveDismiss(direction: DismissDirection.horizontal)
      .toRoute(page: ComplexPage());
    
    Navigator.of(context).push(route);
  }

  Widget _buildTransitionButton(BuildContext context, String title, VoidCallback onTap) {
    return Card(
      child: ListTile(
        title: Text(title),
        trailing: Icon(Icons.arrow_forward_ios),
        onTap: onTap,
      ),
    );
  }
}
```

## 🧪 Testing

### Unit Testing Transitions

```dart
testWidgets('Route transition test', (WidgetTester tester) async {
  // Test your transitions
  await tester.pumpWidget(MyApp());
  
  // Trigger navigation
  await tester.tap(find.text('Navigate'));
  await tester.pump();
  
  // Test animation
  await tester.pump(Duration(milliseconds: 150));
  // Add your assertions here
  
  await tester.pumpAndSettle();
});
```

## 🛠️ Troubleshooting

### Common Issues

1. **Shared elements not working**
   - Ensure both pages have Shifter widgets with the same `shiftId`
   - Check that `sharedElements()` is called in RouteShifterBuilder

2. **Performance issues**
   - Reduce animation duration
   - Limit the number of concurrent effects
   - Use `RepaintBoundary` for complex widgets

3. **Gesture conflicts**
   - Check for conflicting gesture detectors
   - Adjust `dismissThreshold` for interactive dismiss

### Debug Mode

```dart
// Enable debug logging (in debug mode only)
RouteShifterBuilder.debugMode = true;

RouteShifterBuilder()
  .fade()
  .debugInfo() // Prints animation details
  .toRoute(page: NextPage());
```

## 📚 API Reference

### Core Classes

- `RouteShifterBuilder`: Main builder for creating transitions
- `Shifter`: Widget wrapper for shared elements
- `RouteShifter`: Custom PageRoute implementation

### Effect Mixins

- `FadeEffect`: Opacity-based transitions
- `SlideEffect`: Position-based transitions
- `ScaleEffect`: Size-based transitions
- `RotationEffect`: Rotation transformations
- `BlurEffect`: Blur visual effects
- `SharedElementEffect`: Hero-like transitions

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Setup

```bash
git clone https://github.com/yourorg/flutter_route_shifter.git
cd flutter_route_shifter
flutter pub get
cd example
flutter run
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Flutter team for the amazing framework
- Material Design team for design guidelines
- iOS Human Interface Guidelines for Cupertino design
- Community contributors and feedback
- Animation libraries that inspired this package

---

## 🌟 Show Your Support

If you find this package useful, please consider:

- ⭐ Starring the repository
- 🐛 Reporting bugs and issues
- 💡 Suggesting new features
- 🤝 Contributing code
- 📝 Improving documentation

Made with ❤️ for the Flutter community
