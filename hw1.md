<h1>HW1</h1>
    
```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Image("Picture")
                .scaledToFit()
                //.border(.gray)
                .cornerRadius(10)
                .shadow(radius: 3,x:2,y:2)
                .offset(CGSize(width: 0, height: 20))
            Spacer()
                .overlay(ZStack(alignment: .topLeading){
                
                    Text("1103326\n黃玟仁\n希望能夠 All Pass")
                        .multilineTextAlignment(.center)
                        .font(.system(.title, design: .rounded))
                        .shadow(color: .gray, radius: 5, x: 0, y: 0)
                        .frame(width:280, height:130,alignment: .center)
                        .background(Color.white)
                        .opacity(0.9)
                        .border(Color.black)
                    Image(systemName: "person")
                    
                        .font(.largeTitle)
                        .aspectRatio(contentMode: .fill)
                        .imageScale(.large)
                        .foregroundColor(.accentColor)
                        .offset(x:5,y:5)
                })
           
            
            
        }
    }
}
```

<img width="10%"  src="https://github.com/sunnyplaycode/yzu-swiftui-1103326/blob/ebf96abd418602ca18336055121139b94ad96f0c/hw1.jpg">
