# ComposeTooltip
<img width="400" alt="image" src="https://github.com/minwonki/ComposeTooltip/assets/16091736/fc7ee0f0-f365-49d1-b1a3-f1d52575a2bc">

## **Including in your project**

### Gradle

Add the dependency below to your **module**'s `build.gradle` file:

```kotlin
dependencies {
   implementation “com.github.com/**”
}
```

</aside>

## **How to Use**

### Base Example

- Top Tooltip
    
    ```kotlin
    Box() {
    	val openTooltip = remember { mutableStateOf(false) }
    	Button(onclick = { openTooltip.value = true }) {
    	  Text("Top ToolTip")
    	}
    	
    	if (openTooltip.value) {
    		Popup(
          popupPositionProvider = TooltipPositionProvider(
            toolTipPosition = TooltipPosition.Top
          )
        ) {
    	    Tooltip(
              position = TooltipPosition.Top
    	    ) {
           Text(text = "Tooltip")
    	    }
    	  }
    	}
    }
    ```
    
- Left Tooltip
    
    ```kotlin
    Box() {
    	val openTooltip = remember { mutableStateOf(false) }
    	Button(onclick = { openTooltip.value = true }) {
    	  Text("Left ToolTip")
    	}
    	
    	if (openTooltip.value) {
    		Popup(
          popupPositionProvider = TooltipPositionProvider(
            toolTipPosition = TooltipPosition.Left,
    				bias = 0.9f
          )
        ) {
    	    Tooltip(
            position = TooltipPosition.Left
    	    ) {
           Text(text = "Tooltip")
    	    }
    	  }
    	}
    }
    ```
    

### Custom Example

- Tooltip 의 tip 위치를 content 사이즈에 맞게 Custom 할때
- 스크린샷 준비, 코드 준비

### Method signatures

주석으로 대신해도 될듯 함. 주석을 잘 만들어 볼까?

- Tooltip
    
    ```kotlin
    fun Tooltip(
        position: TooltipPosition,
        modifier: Modifier = Modifier,
        cornerRadius: Dp = 10.dp,
        tipWidth: Dp = 6.dp,
        tipHeight: Dp = 6.dp,
        @FloatRange(from = 0.0, to = 1.0) tipBias: Float = 0.5f,
        borderColor: Color = Color.Black,
        bgColor: Color = Color.White,
        contentPadding: Dp = 10.dp,
        elevation: Dp = 2.dp,
        onClick: (() -> Unit)? = null,
        content: @Composable () -> Unit
    )
    ```
    
- TooltipPositionProvider
    
    ```kotlin
    class TooltipPositionProvider(
        val alignment: Alignment = Alignment.Center,
        val toolTipPosition: TooltipPosition = TooltipPosition.Top,
        @FloatRange(from = 0.0, to = 1.0) val bias: Float = 0.5f,
        val offset: IntOffset = IntOffset.Zero
    )
    ```
    

## License

```kotlin
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
