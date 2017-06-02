# GooeyEffect

### Demo
<img  width="200" src="/ReadmeSource/GooeyEffectDemo_.gif" />

main things

the main things of GooeyEffect is :
 - to add movement of the UILabelView from startPoint(UITextField) to endPoint(TagListView) - ‘road path’
 - to add additional shape layer while it moving that will be change its rect path depends of the position on the ‘road-path’ from startPoint to EndPoint
 - endPoint is automatically calculating in TagListView class. we just get this point from the label and pass this label to the GooeyAnimator class

1. Add TagListView and configure it
(about how to configure TagListView see - https://github.com/ElaWorkshop/TagListView)
NOTE: we had did some changes to TagListView component - so please use our edition
<img  width="500" src="/ReadmeSource/addTagListView.png" />


copy TagListView Component:

<img  width="500" src="/ReadmeSource/copyTagListComponent.png" />

2. add tag to the tagListView:
``` swift
// 1 - add new tag to tagListView (this view will be unvisible)
        let tagViewLabel = self.tagListView.addTag(tagText)
```

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
