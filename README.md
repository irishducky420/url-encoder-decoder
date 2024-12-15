### 📢 **Key Features**  
✅ **Shorten URLs** — Instantly create clean, shareable links.  
✅ **Bulk Shorten** — Shorten multiple URLs from a file in one go.  
✅ **Base64 Encode/Decode** — Convert URLs to/from Base64 format.  
✅ **AES Encrypt/Decrypt** — Securely encrypt and decrypt URLs using AES encryption.  
✅ **History Log** — Track and review all past actions.  
✅ **Clipboard Integration** — Automatically copy results for easy sharing.  

Simple. Fast. Secure. 🚀









### 📢 **Feature Message** 
**Introducing the Ultimate URL Shortener & Encoder Tool! 🚀**  
Simplify your URL management with a single, powerful tool. Shorten long URLs, encode or decode in Base64, and keep track of all your actions with a built-in history log. Whether you’re processing one URL or a batch from a file, this tool has you covered. Plus, every link is instantly copied to your clipboard for effortless sharing. No hassle, just results.  


### 📘 **Description of Key Parts**

Here's a breakdown of the key parts of your program, explaining what each section does.

---

#### 🏠 **1. Main Menu** 
**File**: `Main()`  
This is the heart of the program where the user is presented with a menu of six options. It loops continuously until the user selects option `6` (Exit).  

**Options:**
- **1** - Shorten a URL  
- **2** - Bulk shorten URLs from a file  
- **3** - Base64 encode a URL  
- **4** - Base64 decode a URL  
- **5** - View URL history  
- **6** - Exit the application  

**How it works:**  
1. The menu is displayed using `DisplayMenu()`.  
2. The user inputs their choice, and the program calls the appropriate method (like `ShortenSingleURL()` or `BulkShortenURLs()`).  

---

#### ✂️ **2. URL Shortening (Single URL)** 
**File**: `ShortenSingleURL()`  
This method allows users to shorten a single URL using the **TinyURL API**. 

**How it works:**  
1. The user enters a URL.  
2. The program calls the `ShortenURL()` method, which sends an API request to `https://tinyurl.com/api-create.php` with the user's URL.  
3. If successful, the shortened URL is displayed, copied to the clipboard, and saved to the history log.  

**Key Methods Used:**  
- **ShortenURL(url)**: Calls the TinyURL API and returns a shortened URL.  
- **SaveToClipboard(url)**: Automatically copies the shortened URL to the clipboard.  
- **SaveToHistory(action, original, result)**: Logs the shortened URL into a text file (`url_history.txt`).  

---

#### 📁 **3. Bulk URL Shortening (Multiple URLs from a File)** 
**File**: `BulkShortenURLs()`  
This feature processes multiple URLs from a file. If you have many URLs to shorten, this option saves you time by processing them all at once.  

**How it works:**  
1. The user enters the path to a text file containing URLs (one URL per line).  
2. The program reads each line of the file and calls `ShortenURL()` for each URL.  
3. Each shortened URL is saved to the history log and displayed on the console.  

**Key Methods Used:**  
- **File.ReadAllLines(filePath)**: Reads all the URLs from the file.  
- **ShortenURL(url)**: Calls the TinyURL API for each URL.  
- **SaveToHistory(action, original, result)**: Logs each URL and its shortened version to the history file.  

---

#### 🔐 **4. Base64 Encoding (Convert URL to Base64)** 
**File**: `Base64EncodeURL()`  
This feature encodes a URL into a Base64 string. Base64 encoding is often used to make text safe for transmission over the web.  

**How it works:**  
1. The user enters a URL.  
2. The program encodes it using the built-in C# method `Convert.ToBase64String()`.  
3. The Base64 string is displayed, copied to the clipboard, and saved to the history log.  

**Key Methods Used:**  
- **Convert.ToBase64String(Encoding.UTF8.GetBytes(url))**: Encodes the URL into Base64 format.  
- **SaveToClipboard(encodedUrl)**: Copies the Base64-encoded URL to the clipboard.  
- **SaveToHistory(action, original, result)**: Logs the Base64-encoded URL to the history file.  

---

#### 🔓 **5. Base64 Decoding (Convert Base64 to URL)** 
**File**: `Base64DecodeURL()`  
If you have a Base64-encoded URL, this feature allows you to decode it back into its original form.  

**How it works:**  
1. The user enters a Base64-encoded string.  
2. The program decodes it using `Convert.FromBase64String()`.  
3. The decoded URL is displayed, copied to the clipboard, and saved to the history log.  

**Key Methods Used:**  
- **Convert.FromBase64String(encodedUrl)**: Decodes the Base64 string.  
- **SaveToClipboard(decodedUrl)**: Copies the decoded URL to the clipboard.  
- **SaveToHistory(action, original, result)**: Logs the decoded URL to the history file.  

**Error Handling:**  
If the user enters an invalid Base64 string, the program catches the error and prompts them to enter a valid Base64 string.  

---

#### 🕰️ **6. View URL History** 
**File**: `ViewHistory()`  
This feature displays a complete log of every action (shortened, encoded, or decoded URL) the user has performed.  

**How it works:**  
1. The program reads the contents of the `url_history.txt` file.  
2. Each entry in the file is displayed on the console.  

**Log Format:**  
```
[2024-12-15 14:35:23] Shortened: https://example.com -> https://tinyurl.com/abc123
[2024-12-15 14:40:45] Base64 Encoded: https://example.com -> aHR0cHM6Ly9leGFtcGxlLmNvbQ==
```

---

#### 🔥 **7. Reusable Utility Functions** 
These are small helper methods that make the core logic simpler.  

**🌀 ShortenURL(url)**  
- Calls the TinyURL API to generate a short link.  

**📋 SaveToClipboard(text)**  
- Uses the **TextCopy** NuGet package to copy text to the clipboard.  

**📝 SaveToHistory(action, original, result)**  
- Saves each operation (shortened URL, Base64 encoding, etc.) to `url_history.txt`.  

**📂 File Handling**  
- Uses `File.AppendAllText()` to log the history of all operations.  

---

### 🔧 **Possible Enhancements**
If you want to make your URL Shortener Tool even more powerful, consider adding the following features:  
1. **AES Encryption**: Encrypt URLs for secure transmission.  
2. **Custom Short URL Names**: Allow users to customize the short URL name (like tinyurl.com/yourname).  
3. **Error Handling**: Handle file errors (like file not found) more gracefully.  
4. **Export History**: Allow users to export their URL history as a CSV file.  
5. **Cloud Sync**: Sync URL history to the cloud using an API like Google Drive or Dropbox.  

---

### 🔥 **Summary**
Your **URL Shortener & Encoder Tool** is a powerful, all-in-one URL management solution. It allows users to:  
- **Shorten URLs** using TinyURL.  
- **Process bulk URL shortening** from a file.  
- **Base64 encode and decode** URLs.  
- **View all actions in a history log** stored in a file.  
- **Copy results to the clipboard** for fast, easy sharing.  

With a user-friendly menu, automated clipboard copying, and a clean log system, it’s the perfect tool for developers, marketers, and casual users alike. 🚀  

If you'd like help adding features (like AES encryption or cloud sync), I can guide you! 😊
