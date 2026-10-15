# Steam Activate Key Bookmarklet

A lightweight and convenient browser bookmarklet to quickly activate Steam product keys directly from your browser.

Instead of manually navigating to the Steam Store activation page, clicking the bookmarklet prompts you for a key, validates its format, and opens the official Steam key redemption page with your key pre-filled and ready to activate.

---

## Features

- **Instant Activation**: Opens `https://store.steampowered.com/account/registerkey?key=YOUR_KEY` in a new tab with your key pre-filled.
- **Input Validation**: Checks the input against standard Steam key patterns (`AAAAA-BBBBB-CCCCC`).
- **Auto-Capitalization**: Automatically transforms your key to uppercase.
- **Error Handling**: Alerts you if an invalid key format is entered and re-prompts so you can correct it.
- **Graceful Cancellation**: Dismisses cleanly when clicking **Cancel** or pressing `Esc` without opening any windows.
- **Zero Dependencies**: Pure, vanilla JavaScript compatible with any modern web browser (Chrome, Firefox, Edge, Safari, Brave, Opera).

---

## Installation

1. Make sure your browser's **Bookmarks Bar** is visible (press `Ctrl + Shift + B` on Windows/Linux or `Cmd + Shift + B` on macOS).
2. Right-click on your bookmarks bar and select **Add page** or **Add bookmark**.
3. Set the **Name** to `Steam Activate Key` (or any name you prefer).
4. In the **URL** (or **Location**) field, paste the bookmarklet code from [bookmarklet.js](file:///c:/Users/Tati/Documents/Scritps/Steam%20Activate%20Key/bookmarklet.js) (or the snippet below):

```javascript
javascript:(function()%7B'use%20strict'%3B(()%20%3D%3E%20%7Bconst%20baseUrl%20%3D%20'https%3A%2F%2Fstore.steampowered.com%2Faccount%2Fregisterkey%3Fkey%3D'%3Blet%20key%20%3D%20undefined%3Bconst%20regExp%20%3D%20%2F%5E%5Ba-zA-Z0-9%5D%7B5%7D-%5Ba-zA-Z0-9%5D%7B5%7D-%5Ba-zA-Z0-9%5D%7B5%7D%24%2Fmi%3Blet%20error%20%3D%20false%3Bwhile%20(typeof%20key%20!%3D%3D%20'string'%20%7C%7C%20!regExp.test(key))%20%7Bif%20(key%20%3D%3D%3D%20null)%20%7Breturn%3B%7Dif%20(error)%20%7Balert('Invalid%20Steam%20key!')%3B%7D%20else%20%7Berror%20%3D%20true%3B%7Dkey%20%3D%20prompt('Please%20enter%20a%20Steam%20key%3A'%2C%20undefined)%3B%7Dconst%20url%20%3D%20baseUrl%20%2B%20key.toString().toUpperCase()%3Bwindow.open(url%2C'_blank')%3B%7D)()%7D)()
```

5. Click **Save**.

---

## How to Use

1. Click the **Steam Activate Key** bookmarklet on your bookmarks bar.
2. Enter your Steam product key into the popup prompt dialog.
3. Choose an action:
   - **Click OK**: If the key is valid, the Steam activation page opens in a new tab with the key pre-filled. If invalid, an alert will notify you and re-prompt you for a valid key.
   - **Click Cancel**: Closes the dialog immediately.

---

## Supported Key Format

The script validates keys matching standard Steam activation patterns:

- `XXXXX-XXXXX-XXXXX` (3 sets of 5 alphanumeric characters separated by hyphens)

---

## Source Code (Readable)

For transparency and security, here is the readable, unencoded JavaScript source code:

```javascript
(function () {
  'use strict';
  (() => {
    const baseUrl = 'https://store.steampowered.com/account/registerkey?key=';
    let key = undefined;
    const regExp = /^[a-zA-Z0-9]{5}-[a-zA-Z0-9]{5}-[a-zA-Z0-9]{5}$/mi;
    let error = false;

    while (typeof key !== 'string' || !regExp.test(key)) {
      if (key === null) {
        return; // User clicked Cancel
      }
      if (error) {
        alert('Invalid Steam key!');
      } else {
        error = true;
      }
      key = prompt('Please enter a Steam key:', undefined);
    }

    const url = baseUrl + key.toString().toUpperCase();
    window.open(url, '_blank');
  })();
})();
```

---

## License

This project is licensed under the [GNU General Public License v3.0](file:///c:/Users/Tati/Documents/Scritps/Steam%20Activate%20Key/LICENSE).
