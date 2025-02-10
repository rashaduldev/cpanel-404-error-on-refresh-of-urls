# 🚀 Fix React Router 404 Error on cPanel Refresh

## 🛠️ Problem
When deploying a React app on **cPanel**, you might encounter a **404 error** when refreshing or navigating directly to a route. This happens because React uses **client-side routing**, while cPanel's **Apache server** doesn’t automatically serve `index.html` for unknown routes.

---

## ✅ Solution: Configure `.htaccess`
To fix this issue, create or update your `.htaccess` file in your **public_html** directory.

### 📌 **1️⃣ Correct `.htaccess` File**
Copy and paste the following code into your `.htaccess` file:

```apache
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule ^ index.html [L]
</IfModule>
```

---

### 📌 **2️⃣ Steps to Implement**
1️⃣ **Create a `.htaccess` file** (if it doesn’t exist) in your React app’s **build folder**.  
2️⃣ **Paste the above code** inside the `.htaccess` file.  
3️⃣ **Save and upload** the file to the **public_html** directory on cPanel.  

🔹 **Example File Structure After Uploading:**
```
/public_html
   ├── static/
   ├── index.html
   ├── .htaccess  ✅ (File should be here)
   ├── other files...
```

---

### 🖼️ **Visual Guide**
![React Router 404 Fix .htaccess](https://res.cloudinary.com/de8yddexc/image/upload/v1739184333/htaccess/qhkk0gymmvnkefbajdcp.png)

---

## 🎯 Additional Fixes
### 🔹 **Option 1: Set Homepage in `package.json`**
Modify `package.json` to specify the correct base path (especially if your app is in a subfolder):

```json
"homepage": "/"
```
or, if deployed inside `/myapp` folder:
```json
"homepage": "/myapp"
```

---

### 🔹 **Option 2: Use `HashRouter` Instead of `BrowserRouter`**
Modify your `App.js`:
```jsx
import { HashRouter as Router } from "react-router-dom";
```

---

## 🎉 **Final Thoughts**
By following these steps, your React app will work correctly on cPanel without any **404 errors on refresh**. 🚀🔥  

If this guide helped you, give it a ⭐ on GitHub!  
Happy coding! 💻✨