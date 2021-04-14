# bug-removing-NSWindowStyleMaskTitled

Click the button. Then resize the window to be smaller.
Clicking where it USED to be, still activates the window.
Similarly, make the window larger than it was, and clicking in the new space activates the window behind it instead.

Video (fb-only): https://www.internalfb.com/intern/px/p/1GMWJ

```
- (void)onButtonClick:(id)sender {
  self.view.window.styleMask &= ~NSWindowStyleMaskTitled;
}
```

Removing NSWindowStyleMaskTitled after the window's already been created with it causes the issue.
If you create the window without NSWindowStyleMaskTitled, then immediately apply it on load. THEN when you remove it later, it works fine?
