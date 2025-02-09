## JS-Monitor
### Track JavaScript changes websites. Website bot can detected new API endpoints &amp; more!

**Code:**
```python
import requests
from bs4 import BeautifulSoup
import time
URL = "https://example-fintech.com"
CHECK_INTERVAL = 3600 # Check every hour
def fetch_js_urls():
 response = requests.get(URL)
 soup = BeautifulSoup(response.text, "html.parser")
 js_files = [script.get("src") for script in soup.find_all("script") if script.get("src")]
 return js_files
previous_js_files = set(fetch_js_urls())
while True:
 time.sleep(CHECK_INTERVAL)
 current_js_files = set(fetch_js_urls())
 new_files = current_js_files - previous_js_files
 if new_files:
 print("New JavaScript files detected:", new_files)
 previous_js_files = current_js_files
```
