### Android事件分发机制

事件从上至下进行分发，Activity->PhoneWindow->ViewGroup，分别有以步骤：

1. 用户点击屏幕，事件首先传递到屏幕的Activity。Activity调用dispatchTouchEvent进行分发。
   
2. Activity的dispatchTouchEvent方法随后调用Window的superDispatchTouchEvent方法。Window是一个抽象类，其唯一实现类可以在他类的注释里面找到，为PhoneWindow。
   
3. 在PhoneWindow中可以看到其继续调用了DecorView的superDispatchTouchEvent的方法。DecorView继承于FrameLayout->ViewGroup。

4. ACTION_DOWN事件(即多指下的首次按下事件)传递在ViewGroup时，会清除TouchTarget及DisallowOnIntercept标志以及所有的手势等。ViewGroup在ACTION_DOWN事件、以及ViewGroup下子View可处理事件序列时进行拦截（如果子View实现了disallowIntercept时将不会进行拦截，当然，DOWN事件将清除此标志）,如果没有被拦截，则开始正常的事件分发。
    ```Java
    // Check for interception.
    final boolean intercepted;
    if (actionMasked == MotionEvent.ACTION_DOWN
        || mFirstTouchTarget != null) {
            final boolean disallowIntercept = (mGroupFlags & FLAG_DISALLOW_INTERCEPT) != 0;
                if (!disallowIntercept) {
                    intercepted = onInterceptTouchEvent(ev);
                    ev.setAction(action); // restore action in case it was changed
                } else {
                    intercepted = false;
                }
            } else {
                // There are no touch targets and this action is not an initial down
                // so this view group continues to intercept touches.
                intercepted = true;
            }
    ```
5. 当ViewGroup的onInterceptTouchEvent事件为true时，mFirstTouchTarget就为null，则在后续事件将不会再调用onInterceptTouchEvent,ViewGroup将持有后续所有事件。当ViewGroup的子View持有Down事件后，后续事件都会经过intercept，ViewGroup随时可以进行拦截。
    ```Java
   // Dispatch to touch targets.
            if (mFirstTouchTarget == null) {
                // No touch targets so treat this as an ordinary view.
                handled = dispatchTransformedTouchEvent(ev, canceled, null,
                        TouchTarget.ALL_POINTER_IDS);
            } 

            // Perform any necessary transformations and dispatch.
        if (child == null) {
            handled = super.dispatchTouchEvent(transformedEvent);
        } else {
            final float offsetX = mScrollX - child.mLeft;
            final float offsetY = mScrollY - child.mTop;
            transformedEvent.offsetLocation(offsetX, offsetY);
            if (! child.hasIdentityMatrix()) {
                transformedEvent.transform(child.getInverseMatrix());
            }

            handled = child.dispatchTouchEvent(transformedEvent);
        }
   ```
6. 当ViewGroup不拦截事件时，将会向下继续找合适的处理事件的View。如果遍历所有的子元素后事件都没有被合适地处理，这包含两种情况：第一种是ViewGroup没有子元素；第二种是子元素处理了点击事件，但是在dispatchTouchEvent中返回了false，这一般是因为子元素在onTouchEvent中返回了false。在这两种情况下，ViewGroup会自己处理点击事件。
7. 如果找到能够处理事件的view时，事件将由View的dispatchTouchEvent处理。代码如下：
   ```Java
     if (dispatchTransformedTouchEvent(ev, cancelChild,
                                target.child, target.pointerIdBits)) {
                            handled = true;
                        }
   ```
8. View的enable等于false时，只要clickable或longclickable为true，也会消耗事件。当View.setOnTouchListener存在时，会处理调用.onTouch方法，即如果onTouch方法返回值为true时事件被消耗并且不会再执行onTouchEvent方法。事件传递到此即分发完成。

  

