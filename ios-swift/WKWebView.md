### Load webpage in WkWebView
```
        let url = URL(string: "http://www.youtube.com/watch?v=fDXWW5vX-64")
        //let url = URL(string: "https://gcs-vimeo.akamaized.net/exp=1534434268~acl=%2A%2F687898845.mp4%2A~hmac=8f0d06ef85dcdcd6302ab3fe8d98613e47d62a733ff71f45738030a07edd6ea9/vimeo-prod-skyfire-std-us/01/576/8/202884524/687898845.mp4?download=1&filename=Blurred+Bokeh+Video.mp4")
        
        let request = URLRequest(url: url!)
        let webView = WKWebView()
        webView.load(request)
```
