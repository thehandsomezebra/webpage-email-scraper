Certainly! Here's a quick README page for your bookmarklet:

---

# Email Scraper Bookmarklet (Mailto Links Only)

This is a simple JavaScript bookmarklet designed to quickly scrape and copy all email addresses found within `mailto:` links on any webpage.

---

## How it Works

When activated, this bookmarklet does the following:

1.  **Scans for `mailto:` links:** It looks for all `<a>` (anchor) tags whose `href` attribute starts with `mailto:`.
2.  **Extracts email addresses:** From each found `mailto:` link (e.g., `mailto:info@example.com?subject=Hello`), it extracts just the email address part.
3.  **Removes duplicates:** It collects all unique email addresses.
4.  **Copies to clipboard:** All unique email addresses are then copied to your clipboard, each on a new line.
5.  **Provides feedback:** You'll receive an alert indicating whether emails were copied or if none were found.

---

## Installation

1.  **Copy the Bookmarklet Code:**
    Click the little clipboard icon to the far right of the code box. ((If that icon is not available, highlight the code and CTRL + C [copy]))

    ```javascript
    javascript:(function() {    function copyToClipboard(text) {        const textarea = document.createElement('textarea');        textarea.value = text;        document.body.appendChild(textarea);        textarea.select();        document.execCommand('copy');        document.body.removeChild(textarea);        alert('Email addresses copied to clipboard!');    }    const emailAddresses = new Set();    document.querySelectorAll('a[href^="mailto:"]').forEach(link => {        const email = link.href.split(':')[1].split('?%27)[0];         if (email) {            emailAddresses.add(email);        }    });    if (emailAddresses.size > 0) {        const emailsString = Array.from(emailAddresses).join(%27\n%27);        copyToClipboard(emailsString);    } else {        alert(%27No mailto: links with email addresses found on this page.%27);    }})();
    ```

2.  **Create a New Bookmark in Your Browser:**
    * **Google Chrome:**
        * Right-click on your bookmarks bar and select "Add Page" or go to `chrome://bookmarks/` and click the three dots in the top right, then "Add new bookmark."
    * **Mozilla Firefox:**
        * Right-click on your bookmarks toolbar and select "New Bookmark..." or go to `about:bookmarks` (Library) and click "Organize" -> "New Bookmark...".
    * **Microsoft Edge:**
        * Right-click on your favorites bar and select "Add new favorite" or go to `edge://favorites/` and click "Add favorite."

3.  **Configure the Bookmark:**
    * **Name:** Give it a memorable name, like "Scrape Emails"
    * **URL/Address:** Paste the JavaScript code you copied in step 1 into this field.
    * **Save:** Click "Save" or "Done."

---

## Usage

1.  Navigate to any webpage where you want to extract email addresses from `mailto:` links.
2.  Click on the "Scrape Mailto Emails" bookmark you just created in your browser's bookmarks bar or menu.
3.  An alert will pop up, confirming that the email addresses have been copied to your clipboard.

---

## Limitations

* This bookmarklet *only* extracts email addresses from `mailto:` links. It will not find email addresses that are simply displayed as plain text on the page without a `mailto:` link.
* It relies on the browser's `document.execCommand('copy')` which might have limitations or require user interaction in some strict browser security settings, though it generally works well for bookmarklets.

---

## Version

Version 1. May 21, 2025