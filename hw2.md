<h1>HW2</h1>

```swift

import SwiftUI

struct ContentView: View {
    @State var randomInt=0
    @State var str:String="剪刀"
    var body: some View {
        Text(str)
            .font(.system(size: 100))
        Button {
            randomInt=Int.random(in:0...2)
            switch randomInt {
            case 0:
                str="剪刀"
            case 1:
                str="石頭"
            default:
                str="布"
            }
        }label:{
            Text("Go!!!")
                //.font(.largeTitle)
                .font(.system(size: 60))
        }
        .buttonStyle(.borderedProminent)
        .buttonBorderShape(.capsule)
    }
}
```

<img width="40%"  src="https://github.com/sunnyplaycode/yzu-swiftui-1103326/blob/418eda63fd42d5ab22071d5e8cc49dc99e8d355c/hw2.jpg">
