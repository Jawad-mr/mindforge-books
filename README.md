# PageVault

Static bookstore demo built in `index.html`.

## What changed
- Admin access is routed through `/admin`.
- The admin screen is locked behind PIN `1234`.
- The reading flow is gated so books must be purchased before opening the reader.
- Emoji UI was replaced with Font Awesome icons.

## Firebase Hosting setup
1. Install the Firebase CLI:

```bash
npm install -g firebase-tools
```

2. Sign in:

```bash
firebase login
```

3. Initialize hosting in this folder if needed:

```bash
firebase init hosting
```

4. Use these answers when prompted:
- Public directory: `.`
- Configure as a single-page app: `Yes`
- Set up automatic builds/deploys: `No` for this static demo

5. Deploy:

```bash
firebase deploy
```

The included `firebase.json` rewrites all routes to `index.html`, so direct links like `/admin` will still load correctly.

## Razorpay setup
1. Create a Razorpay account and generate your **Key ID** and **Key Secret**.
2. Add a checkout button or script in your backend or a serverless function, not directly in the browser for production.
3. Create an order from your backend using the Razorpay Orders API.
4. Pass the order ID to the Razorpay Checkout script.
5. On successful payment, verify the payment signature on the server.
6. Only after verification should you unlock the purchased book or mark the order as paid.

Recommended flow for this app:
- `Buy Now` adds the book to cart.
- Checkout sends the order to your backend.
- Backend creates the Razorpay order.
- After payment success, mark the book as purchased and allow `Read`.

## Admin access
- Open `/admin`
- Enter PIN `1234`

## Notes
- This is still a frontend-only demo until you connect Firebase services and Razorpay verification on the backend.
