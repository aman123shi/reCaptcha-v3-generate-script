```markdown
# reCAPTCHA v3 Token Generator

A simple HTML page that generates reCAPTCHA v3 tokens for testing backend verification with tools like Postman.

## Features

- Generates reCAPTCHA v3 tokens with a single click
- Copy token functionality for easy testing
- Instructions for backend verification
- Clean, responsive interface

## Prerequisites

1. A reCAPTCHA v3 site key from [Google reCAPTCHA Admin](https://www.google.com/recaptcha/admin/)
2. The domain you're testing from must be registered in your reCAPTCHA admin settings

## Setup

1. Clone this repository
2. Open `index.html` in a code editor
3. Replace `YOUR_SITE_KEY` (two occurrences) with your actual reCAPTCHA v3 site key
4. Save the file

## Usage

1. Open `index.html` in a browser
2. Click "Generate reCAPTCHA Token" button
3. Copy the generated token using the "Copy Token" button
4. Use this token in your backend verification tests

## Backend Verification

To verify the token in your backend:

1. Make a POST request to: `https://www.google.com/recaptcha/api/siteverify`
2. Include these parameters:
   - `secret`: Your reCAPTCHA secret key (from admin console)
   - `response`: The token you copied

### Example Postman Request

```
POST https://www.google.com/recaptcha/api/siteverify
Content-Type: application/x-www-form-urlencoded

secret=YOUR_SECRET_KEY&response=COPIED_TOKEN
```

### Example Response

```json
{
  "success": true,
  "score": 0.9,
  "action": "submit",
  "challenge_ts": "2023-06-01T12:34:56Z",
  "hostname": "yourdomain.com"
}
```

## Important Notes

- Tokens expire after ~2 minutes
- Never expose your secret key in client-side code
- The verification must be done server-side
- Recommended score threshold is typically 0.5 (adjust based on your needs)

## License

This project is open source and available under the [MIT License](LICENSE).

```
