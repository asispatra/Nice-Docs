### Load webpage in WKWebView
```
        let url = URL(string: "http://www.youtube.com/watch?v=fDXWW5vX-64")
        
        let request = URLRequest(url: url!)
        let webView = WKWebView()
        webView.load(request)
```

### Embed youtube video in WKWebView
```
        let webView = WKWebView()
        let youtubeVideolink = "https://www.youtube.com/embed/Rg6GLVUnnpM"

        let bounds = UIScreen.main.bounds
        let width = bounds.size.width - 18
        let height = bounds.size.width / 1.8
        let frame = 0
        let code = "<iframe width=\(width) height=\(height) src=\(youtubeVideolink) frameborder=\(frame) allowfullscreen></iframe>"

        webView.loadHTMLString(code, baseURL: nil)
        safeAreaView.addSubview(webView)
```
