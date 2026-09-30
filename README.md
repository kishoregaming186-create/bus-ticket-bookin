# bus-ticket-bookin
its a bus ticket booking website
import http.server
import socketserver
import webbrowser

PORT = 8000

class Handler(http.server.SimpleHTTPRequestHandler):
    def do_GET(self):
        if self.path == "/":
            self.path = "/busgo.html"
        return super().do_GET()

with socketserver.TCPServer(("", PORT), Handler) as server:
    url = f"http://localhost:{PORT}"
    print(f"BusGo running at {url}  (press Ctrl+C to stop)")
    webbrowser.open(url)
    server.serve_forever()
