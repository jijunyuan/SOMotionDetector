SOMotionDetector
================

Simple library to detect motion for iOS by <b> arturdev </b>.

Based on location updates and acceleration.

Compatible with iOS 7

USAGE
=====
Copy <b>SOMotionDetector</b> folder to your project.

Link <b>CoreMotion.framework</b>, <b>CoreLocation.framework</b>.

Import <b>SOMotionDetector.h"</b> file and implement <br><SOMotionDetectorDelegate></b> protocol.

```ObjC
#import "SOMotionDetector.h
@interface ViewController ()<SOMotionDetectorDelegate>

@end
```

Set SOMotionDetector's delegate to self
```ObjC
[SOMotionDetector sharedInstance].delegate = self;
```

Implement delegate methods 
```ObjC
- (void)motionDetector:(SOMotionDetector *)motionDetector motionTypeChanged:(SOMotionType)motionType
{

}

- (void)motionDetector:(SOMotionDetector *)motionDetector locationChanged:(CLLocation *)location
{

}

- (void)motionDetector:(SOMotionDetector *)motionDetector accelerationChanged:(CMAcceleration)acceleration
{
    
}
```

You are done! 

Now to start detection motion just call
```ObjC 
[[SOMotionDetector sharedInstance] startDetection];
```

To stop detection call
```ObjC 
[[SOMotionDetector sharedInstance] stopDetection];
```  

###Detecting motion types
```ObjC
typedef enum
{
  MotionTypeNotMoving = 1,
  MotionTypeWalking,
  MotionTypeRunning,
  MotionTypeAutomotive
} SOMotionType;
```

CUSTOMIZATION
=============
```ObjC

/**
 *@param speed  The minimum speed value less than which will be considered as not moving state
 */
- (void)setMinimumSpeed:(CGFloat)speed;

/**
 *@param speed  The maximum speed value more than which will be considered as running state
 */
- (void)setMaximumWalkingSpeed:(CGFloat)speed;

/**
 *@param speed  The maximum speed value more than which will be considered as automotive state
 */
- (void)setMaximumRunningSpeed:(CGFloat)speed;

/**
 *@param acceleration  The minimum acceleration value less than which will be considered as non shaking state
 */
- (void)setMinimumRunningAcceleration:(CGFloat)acceleration;

```