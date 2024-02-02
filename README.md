import SwiftUI
import UserNotifications
import UserNotificationsUI
import NotificationCenter

struct ContentView: View {
    var body: some View {
        VStack {
            Button("request permisson") {
                UNUserNotificationCenter.current().requestAuthorization(options: [ .alert,.badge, .sound]) { success, error in
                    if success  {
                        print("all sets")
                    } else if let error {
                        print(error.localizedDescription)
                    }
                    }
            }
            Button("schedule notifcation ") {
             let content = UNMutableNotificationContent()
                content.title = "feed the cat "
                content.subtitle = "it looks hungry "
                content.title = "doherdhsohehs"
                content.sound = UNNotificationSound.default
                
                let trigger = UNTimeIntervalNotificationTrigger(timeInterval: 5, repeats: false)
                
                let request = UNNotificationRequest(identifier: UUID().uuidString,content:  content, trigger: trigger)
               
                UNUserNotificationCenter.current().add(request)
            }
        }
        .padding()
    }
}

#Preview {
    ContentView()
}
