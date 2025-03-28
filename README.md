# Google-Recaptcha-documentation

### Step 01: Go to [react-google-recaptcha](https://www.npmjs.com/package/react-google-recaptcha) and install the package.

```javascript
npm install --save react-google-recaptcha
```

### Step 02: Go to [GooGle-reCAPTCHA](https://www.google.com/recaptcha/admin/create) and configure the Google reCAPTCHA page.

![Markdown](https://res.cloudinary.com/dvqqxighm/image/upload/v1742362279/recaptcha_kuzzvr.png)

### Step 03: Create .env file into root directory

```javascript
NEXT_PUBLIC_CLIENT_RECAPTCHA = 6LfEGvkqAAAAAMu0uHwWbZ7DcOdUzD9YFzTLTgLo
NEXT_PUBLIC_SERVER_RECAPTCHA = 6LfEGvkqAAAAAOcKXBBR8-xTkAUJVUiEeR8v7ixW
```

### Step 04: Import recaptha and use ReCAPTCHA component

```javascript
import ReCAPTCHA from "react-google-recaptcha";
<ReCAPTCHA
  sitekey={`${process.env.NEXT_PUBLIC_CLIENT_RECAPTCHA}`}
  onChange={handleRecaptcha}
/>;
```

### Step 05: Create an uitls function to verify the reCAPTCHA

```javascript
export const reCaptchaTokenVerification = async (token: string) => {
  try {
    const res = await fetch("https://www.google.com/recaptcha/api/siteverify", {
      method: "POST",
      headers: {
        "Content-Type": "application/x-www-form-urlencoded",
      },
      body: new URLSearchParams({
        secret: process.env.NEXT_PUBLIC_SERVER_RECAPTCHA!,
        response: token,
      }),
    });

    return res.json();
  } catch (err: any) {
    return Error(err);
  }
};
/>
```
