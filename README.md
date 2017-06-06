# GooeyEffect

### Demo
<img  width="200" src="/ReadmeSource/GooeyEffectDemo_.gif" />

main things:

 - the main things of GooeyEffect is to add movement of the some UIView from startPosition(initialPoint) to the endPosition(toPoint) with special GooeyEffect
 - all actions should be happens in a specified containerView (UIView) while animating, so the startPosition/endPosition points should be converted to coordinate system of the containerView before animation will be started
 - an additional shapeLayer from GooeyEffectView class will be redrawn each time when animationView will be moved while animating
 - in our DemoApp the endPosition is automatically calculating in TagListView class. we just get this point from the TagView for converting to coordinate system of containerView and pass it to GooeyAnimator


### USAGE

1. Add TagListView and configure it
(about how to configure TagListView see - https://github.com/ElaWorkshop/TagListView)
NOTE: we had did some changes to TagListView component - so please use our edition if you wants to have the same idea of usage GooeyEffect

<img  width="500" src="/ReadmeSource/addTagListView.png" />

and copy TagListView Component:

<img  width="500" src="/ReadmeSource/copyTagListComponent.png" />

2. add new tag to tagListView (this view will be setted invisible before animation and visible right animation did end):

``` swift
// 1 - add new tag to tagListView (this view will be unvisible)
        let tagViewLabel = self.tagListView.addTag(tagText)
```
3. prepare startPosition and endPosition - convert these points to coordinate system of containerView (in our DemoApp it is self.view)

``` swift
``` 

4. create GooeyAnimator instance 


3. create UILabel from TagView and pass it to GooeyAnimator. Set Up parameters and call animate() function
``` swift
//
    // animate lable movement with gooeyEffect
    // - create visible label that contain the same parameters of TagView
    // - pass label and tagsTextField to the GooeyAnimator
    // - set up duration and delegate for GooeyAnimator
    // - animate label
    //
    private func addAnimationToTagView(tagView: TagView) {
        if let frame = tagView.absoluteFrame {
            let label = UILabel(frame: frame)
            label.text = tagView.titleLabel?.text
            label.textAlignment = .center
            label.font = tagView.textFont
            label.textColor = tagView.textColor
            label.backgroundColor = tagView.backgroundColor
            label.layer.cornerRadius = tagView.cornerRadius
            label.isOpaque = true
            label.clipsToBounds = true
            self.tagListView.addSubview(label)
            self.tagLabels.append(label)
            
            let animator = GooeyAnimator(frame: self.view.frame, messageLable: label, textField: self.tagsTextField)
            self.view.addSubview(animator)
            animator.duration = 0.8
            animator.delegate = self
            
            animator.animate()
        }
    }
```

4. GooeyAnimatorDelegate - you can follow events in GooeyAnimator class in functions:
``` swift
//MARK: GooeyAnimatorDelegate
    
    func onAnimation(_ actualFrame: CGRect) {
    }
    
    func onStartAnimation() {
    }
    
    func onStopAnimation(_ label: UILabel) {
    }
```

6. start animation  - just call fire() method

``` swift
``` 

