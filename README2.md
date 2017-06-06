# GooeyEffect

### DEMO

<img  width="200" src="/ReadmeSource/gooeyDemo_356_200.gif" />

### USAGE
**1. Create GooeyAnimator instance**

``` swift
let animator = GooeyAnimator.addAnimation(toContainerView: self.view, 
                                          animateView: tagView, 
                                          toPoint: point, 
                                          duration: 0.8, 
                                          baseView: self.tagsTextField)
``` 

**2. Start animation**
* To start gooey animation call **fire()** method

``` swift
animator.fire()
``` 

**3.** [Optional] **Delegate**
* Set the delegate if you want to folow events

``` swift
{
    animator.delegate = self
    animator.fire()
}
```

* You can follow events from GooeyAnimator class in the next functions:
``` swift
//MARK: GooeyAnimatorDelegate
    
func gooeyAnimatorDidStartAnimation(_ gooeyAnimator: GooeyAnimator) {
}
   
func gooeyAnimator(_ gooeyAnimator: GooeyAnimator, didStopAnimateView animatedView: UIView) {
}

func gooeyAnimator(_ gooeyAnimator: GooeyAnimator, didAnimateView animatedView: UIView, toPosition position: CGPoint) {
}
```
 

### NOTES

 * The main things of GooeyEffect is to add movement to some UIView (animationView) from start position (initial point) to the end position (toPoint) with special GooeyEffect
 * All actions should be happens in a specified containerView (UIView) while animating, so the initial and destination points should be converted to containerView coordinate system before animation will be started
 * An additional shapeLayer from GooeyEffectView class will be redrawn each time when animationView will be moved while animating
 * Initial position is taken from animationView. So it should be set before animation start


### STRUCTURE

1. Parameters
* **containerView** - GooeyAnimator will be added to containerView with same frame (bounds)
* **animateView** - this view will be animated with gooey effect added to it. animateView will be added to GooeyAnimator view. animateView origin position should be set to initial value in GooeyAnimator (or containerView) coordinate system
* **toPoint** (destinationPoint) - end (final) point of gooey animation. Should be in GooeyAnimator (or containerView) coordinate system
* **duration** - time for which animateView will be moved from initial position to destination point
* **baseView** - this is a second view gooey effect will be applyed to. baseView is not moved by GooeyAnimator

<img  width="500" src="/ReadmeSource/gooeyEffectViewsStructure.png" />


### TIPS

1. Convert all points to containerView coordinate system (self.view in example)
``` swift
let initialPoint = self.tagsTextField.superview?.convert(self.tagsTextField.frame.origin, to: self.view)
let toPoint = self.tagListView?.convert(tagView.frame.origin, to: self.view) 
```

2. Setup animationView to initial point before animation
``` swift
animationView.frame.origin = initialPoint
``` 

That's it! join to GooeyEffect!

