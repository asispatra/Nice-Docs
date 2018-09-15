### Load webpage in WkWebView
```
        let url = URL(string: "http://www.youtube.com/watch?v=fDXWW5vX-64")
        
        let request = URLRequest(url: url!)
        let webView = WKWebView()
        webView.load(request)
```
