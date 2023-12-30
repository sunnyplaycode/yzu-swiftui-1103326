<h1>HW4</h1>

```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Text("我的旅行規劃")
                .font(.largeTitle)
                .fontWeight(.heavy)
                .foregroundStyle(.primary)
                .padding(.top,30)
            TabView{
                Group{
                    WelcomeView()
                        .tabItem { 
                            Image(systemName: "house.fill")
                            Text("Home")
                        }
                    TripView()
                        .tabItem {
                            Image(systemName: "suitcase.rolling")
                            Text("Trip")
                        }

                    PrepareView()
                        .tabItem { 
                            Image(systemName: "list.dash")
                            Text("Prepare")
                        }
                

                }
                .toolbarBackground(Color.white, for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)
                //.toolbarColorScheme(.dark, for: .tabBar)
            }
            .tint(.cyan)
        }
    }
}


struct WelcomeView: View {
    var body: some View {
        VStack{
            Image("home_pic")
                .resizable()
                .aspectRatio(contentMode: .fit)
                
            Text("我是一個喜歡旅遊的人\n覺得人生從不該只停留在一個地方\nThe world is a book,\nbuy people do not travel\nread only one page")
                .fontWeight(.bold)
                .frame(width:350,height: 190,alignment: .center)
                //.background(.blue)
                //.font(.system(.largeTitle,design: .rounded))
                .font(.system(size:20))
                .lineSpacing(10)
                .padding()

            Text("作者:黃玟仁\n更新日期:2023/12/31")
                .fontWeight(.medium)
                .foregroundColor(.black)
                .frame(width: 330,height: 50,alignment: .bottomLeading)
                //.background(Color.black)
                //.cornerRadius(20)
                //.multilineTextAlignment(.center)
            
        }
    }
}

struct PrepareView: View {
    @State var idcard = false
    @State var wallet = false
    @State var cloths = false
    @State var phone = false
    @State var paper = false
    @State var camera = false
    @State var computer = false
    @State var headset = false
    
    @State var teethbrush = false
    @State var towel = false
    @State var eye = false
    @State var facewash = false
    @State var makeup = false
    
    @State var clo = false
    @State var medicine = false
    @State var umb = false
    @State var bag = false
    @State var knife = false
    var body: some View {
        NavigationView{
            Form(content: {
                Section(header: Text("必備品"),
                        content:{
                    Toggle(isOn: $idcard,
                           label:{Text("個人證件(身分證,護照,駕照)")})
                    Toggle(isOn: $wallet,
                           label:{Text("錢包")})
                    Toggle(isOn: $cloths,
                           label:{Text("換洗衣物")})
                    Toggle(isOn: $phone,
                           label:{Text("手機&充電線&行充")})  
                    Toggle(isOn: $paper,
                           label:{Text("旅行相關文件")})  
                })
                Section(header: Text("3C產品"),
                        content:{
                    Toggle(isOn: $camera,
                           label:{Text("相機")})
                    Toggle(isOn: $computer,
                           label:{Text("電腦")})
                    Toggle(isOn: $headset,
                           label:{Text("耳機")}) 
                })
                Section(header: Text("盥洗用品"),
                        content:{
                    Toggle(isOn: $teethbrush,
                           label:{Text("牙刷&牙膏")})
                    Toggle(isOn: $towel,
                           label:{Text("毛巾")})
                    Toggle(isOn: $makeup,
                           label:{Text("化妝品")}) 
                    Toggle(isOn: $eye,
                           label:{Text("隱眼")}) 
                    Toggle(isOn: $facewash,
                           label:{Text("洗面乳")}) 
                })
                
                Section(header: Text("雜物類"),
                        content:{
                    Toggle(isOn: $clo,
                           label:{Text("衣架")})
                    Toggle(isOn: $medicine,
                           label:{Text("常備藥品")})
                    Toggle(isOn: $umb,
                           label:{Text("雨傘")}) 
                    Toggle(isOn: $bag,
                           label:{Text("折疊式袋子")}) 
                    Toggle(isOn: $knife,
                           label:{Text("瑞士刀")}) 
                })
            })
            
        }
    }
    
}
struct Trip: Identifiable{
    var id = UUID()
    var image: String
    var name: String
    var description: String
}
var trips = [
    Trip(image: "sunmoonlake", name: "日月潭三日遊", description: "2023/10/8~10\n環湖自行車欣賞風景\n南投周邊景點遊玩"),
    Trip(image: "tamsui", name: "淡水一日遊", description: "2023/11/18\n夕陽很美\n魚酥很好吃！\n記得買多一點"),
    Trip(image: "kao", name: "高雄跨年行", description: "2023/12/31\n與家人於旁邊夢時代購物\n結束後前往場地佔位"),
    Trip(image: "osaka", name: "(國外)大阪自由行", description: "2022/7/3~9\n心齋橋道頓掘\n環球影城\n大阪城\n海遊館\n有鯨鯊！！！！"),
    Trip(image: "sing", name: "(國外預計)新加坡旅行團", description: "2024 暑假(預計)\n帆船飯店\n聖淘沙"),
    Trip(image: "hong", name: "(國外預計)香港找親戚之旅", description: "2025 寒假(預計)\n深圳\n香港美食\n維多利亞港夜景")
    
]
struct BasicImageRow: View {
    var thisTrip:Trip
    var body: some View {
        HStack{
            Image(thisTrip.image)
                .resizable()
                .frame(width: 70,height: 60)
                .cornerRadius(3)
            Text(thisTrip.name)
                .bold()
        }
    }
}
struct TripDetailView: View{
    @Environment(\.presentationMode) var presentationMode
    var thisTrip:Trip
    var body: some View{
        ScrollView{
            VStack{
                Image(thisTrip.image)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisTrip.name)
                    .font(.system(.title, design: .rounded))
                    .fontWeight(.black)
                //.font(.title)
                Spacer()
                Text(thisTrip.description)
                //.font(.system(.subheadline,design: .rounded))
                    .fontWeight(.light)
                    .font(.system(size:20))
                Spacer()
            }
        }
        .overlay(
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label: {
                        Image(systemName:"xmark")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                        
                    })
                    .padding(.trailing,20)
                    .padding(.top, 40)
                    Spacer()
                }
            })
    }
}

struct TripView: View {
    @State var showDetailView = false
    @State var selectedTrip:Trip?
    var body: some View {
        NavigationView{
            List(trips){ TripItem in
                BasicImageRow(thisTrip: TripItem)
                    .onTapGesture {
                        self.showDetailView = true
                        self.selectedTrip = TripItem
                    }
            }
            .sheet(item: self.$selectedTrip){ thisTrip in
                TripDetailView(thisTrip: thisTrip)    
            }
            .navigationBarTitle("旅遊清單")
            
        }
    }
}
```
<img width="40%"  src="https://github.com/sunnyplaycode/yzu-swiftui-1103326/blob/fee9e63ed7e5f9ed52ba50284cbcae02f91e59e1/hw4-1.jpg">
<img width="40%"  src="https://github.com/sunnyplaycode/yzu-swiftui-1103326/blob/fee9e63ed7e5f9ed52ba50284cbcae02f91e59e1/hw4-2.jpg">
<img width="40%"  src="https://github.com/sunnyplaycode/yzu-swiftui-1103326/blob/fee9e63ed7e5f9ed52ba50284cbcae02f91e59e1/hw4-3.jpg">
<img width="40%"  src="https://github.com/sunnyplaycode/yzu-swiftui-1103326/blob/fee9e63ed7e5f9ed52ba50284cbcae02f91e59e1/hw4-4.jpg">




