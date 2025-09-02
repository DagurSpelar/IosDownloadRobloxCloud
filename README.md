# iOS Profile Mini-Site

Files:
- `index.html` — shows an **iOS** button.
- `install.html` — immediately redirects to the profile and provides a fallback button.
- `GetMC.mobileconfig` — your configuration profile.
- `.htaccess` — sets the correct MIME type for Apache/htaccess-compatible hosts.

## How it works
1. Your homepage (`index.html`) has an **Install on iOS** button linking to `install.html`.
2. `install.html` auto-redirects the browser to `GetMC.mobileconfig`. On iOS Safari, this triggers the native profile prompt.
3. If the auto-redirect is blocked, the page shows a big **Download Profile** button as fallback.

## Deploy
Upload all files to the same folder on your server or hosting.
If you’re using Nginx or another server type, set the content-type for `.mobileconfig` to `application/x-apple-aspen-config`.

### Nginx example
```
types {
  application/x-apple-aspen-config  mobileconfig;
}
```

### Notes
- On iOS, users will see an **Allow** prompt, then finish installation in **Settings → Profile Downloaded**.
- Keep the file name `GetMC.mobileconfig` consistent with the links in the HTML.
