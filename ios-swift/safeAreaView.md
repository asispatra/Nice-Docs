### ios app without story board
```
class AppDelegate: UIResponder, UIApplicationDelegate {

    var window: UIWindow?

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.
        self.window = self.window ?? UIWindow()
        self.window!.backgroundColor = .white
        self.window!.rootViewController = UINavigationController(rootViewController: ViewController())
        self.window!.makeKeyAndVisible()
        return true
    }
```

### SafeAreaView with WKWebView
```
import UIKit
import WebKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        setupSafeAreaView()
        
        let url = URL(string: "http://www.youtube.com/watch?v=fDXWW5vX-64")
        
        let request = URLRequest(url: url!)
        let webView = WKWebView()
        webView.load(request)
        safeAreaView.addSubview(webView)
        
        webView.translatesAutoresizingMaskIntoConstraints = false
        
        let d = ["bar":webView]
        NSLayoutConstraint.activate([
            NSLayoutConstraint.constraints(withVisualFormat:
                "H:|[bar]|", metrics: nil, views: d),
            NSLayoutConstraint.constraints(withVisualFormat:
                "V:|[bar]|", metrics: nil, views: d)
            ].flatMap{$0})
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }

    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        navigationController?.setNavigationBarHidden(true, animated: animated)
    }
    
    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        navigationController?.setNavigationBarHidden(false, animated: animated)
    }

    let safeAreaView = UIView()
    func setupSafeAreaView() {
        safeAreaView.translatesAutoresizingMaskIntoConstraints = false
        //safeAreaView.backgroundColor = .green
        view.addSubview(safeAreaView)
        
        if #available(iOS 11, *) {
            let guide = view.safeAreaLayoutGuide
            NSLayoutConstraint.activate([
                safeAreaView.leftAnchor.constraintEqualToSystemSpacingAfter(guide.leftAnchor, multiplier: 0.0),
                guide.rightAnchor.constraintEqualToSystemSpacingAfter(safeAreaView.rightAnchor, multiplier: 0.0)
                ])
            NSLayoutConstraint.activate([
                safeAreaView.topAnchor.constraintEqualToSystemSpacingBelow(guide.topAnchor, multiplier: 0.0),
                guide.bottomAnchor.constraintEqualToSystemSpacingBelow(safeAreaView.bottomAnchor, multiplier: 0.0)
                ])
            
        } else {
            let standardSpacing: CGFloat = 8.0
            // TODO: Manage left and right side of the Safe Area
            NSLayoutConstraint.activate([
                safeAreaView.topAnchor.constraint(equalTo: topLayoutGuide.bottomAnchor, constant: standardSpacing),
                bottomLayoutGuide.topAnchor.constraint(equalTo: safeAreaView.bottomAnchor, constant: standardSpacing)
                ])
        }
    }
}
```
