# Backend Notes

## Understanding Refresh Tokens vs. Access Tokens

In many web apps, we use two types of tokens to keep users logged in: **access tokens** and **refresh tokens**. Here’s what they are and how they're different:

### Access Token
- **What it does:** Lets you access secure parts of the app.
- **How long it lasts:** Only for a short time (a few minutes to a few hours).
- **Where it's stored:** Usually in your browser's memory.
- **Why it’s important:** It’s short-lived, so if someone steals it, they can't use it for long.

### Refresh Token
- **What it does:** Lets you get a new access token without logging in again.
- **How long it lasts:** For a long time (days, weeks, or even months).
- **Where it's stored:** In a safe place, like a secure cookie.
- **Why it’s important:** It helps you stay logged in without putting your account at risk.

### Why Use Both?
- **Access tokens** are short-lived, making them safer because they don’t stay valid for long if stolen.
- **Refresh tokens** let you get new access tokens easily, so you don’t have to keep logging in.

---

## How Refresh Tokens Work

When you log into an app, it often gives you two tokens: an **access token** and a **refresh token**. Here’s how the refresh token works step-by-step:

1. **Login:** When you first log in, the server gives you both an access token and a refresh token.
2. **Using the Access Token:** You use the access token to access secure parts of the app. This token has a short life and will expire soon.
3. **Access Token Expires:** When the access token expires, you can’t access secure parts of the app anymore.
4. **Using the Refresh Token:** Instead of logging in again, your app sends the refresh token to the server.
5. **Server Verifies:** The server checks the refresh token. If it’s valid, the server issues a new access token.
6. **Getting a New Access Token:** Your app receives the new access token and can continue accessing secure parts of the app without asking you to log in again.
7. **Repeat:** This process can repeat until the refresh token itself expires, which is usually after a much longer period.

### Example with Instagram

- **Initial Login:** You log into Instagram and get both tokens.
- **Access Token Expires:** After some time, the access token expires.
- **Automatic Renewal:** The app uses the refresh token to get a new access token without you logging in again.

This method ensures a secure and smooth user experience.

---

## Security Measures
- **Secure Storage:** Tokens are stored securely both on the client and server to prevent unauthorized access.
- **Token Rotation:** Sometimes, servers issue a new refresh token along with a new access token to further reduce the risk of misuse.
- **Revocation:** Servers can invalidate refresh tokens if needed, such as when a user logs out or if suspicious activity is detected.

By following these steps, the server ensures that only valid, unexpired, and authorized refresh tokens can be used to get new access tokens, keeping your sessions secure.
