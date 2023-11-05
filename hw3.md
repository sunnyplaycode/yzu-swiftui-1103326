<h1>HW3</h1>

```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack (alignment: .center, spacing: 2) {
            TitleView()
            HStack{
                PictureView(imageName: "aurora")
                PictureView(imageName: "hot air ballon")
                PictureView(imageName: "lake")
            }
            HStack{
                PictureView(imageName: "mountain")
                PictureView(imageName: "pond")
                PictureView(imageName: "promontory")
            }
            HStack{
                PictureView(imageName: "snow Mt.")
                PictureView(imageName: "starry sky")
                PictureView(imageName: "sunrise")
            }
            
        }
    }
}
struct TitleView: View {
    var body: some View {
        VStack(alignment: .center, spacing:2) {
            Text("黃玟仁的")
                .font(.title)
            Text("風景相簿")
                .font(.title)
        }
    }
}
struct PictureView: View {
    var imageName:String
    var body: some View {
        VStack{
            Image(imageName)
                .resizable()
                //.aspectRatio(contentMode: .fit)
                .frame(height:120,alignment: .center)

            Text(imageName.capitalized)
                .fontWeight(.bold)
                .font(.system(size: 15))
        }.padding(.all, 10)
    }
}

```

