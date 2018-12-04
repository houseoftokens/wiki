---
title: Google Authenticator
chapter: 1
layout: default
---

# Google Authenticator

Google Authenticator is a software token that implements two-step verification services using the Time-based One-time Password Algorithm (TOTP) and HMAC-based One-time Password algorithm (HOTP), for authenticating users of mobile applications by Google. The service implements algorithms specified in RFC 6238 and RFC 4226, respectively.

Authenticator provides a six- to eight-digit one-time password which users must provide in addition to their username and password to log into Google services or other sites. The Authenticator can also generate codes for third-party applications, such as password managers or file hosting services. Previous versions of the software were open-sourced but subsequent releases are proprietary.

## Main Information

Title | Description
 --- | --- 
 Developer(s) | Google
 Initial release | September 20, 2010; 
 Repository | [github.com/google/google-authenticator](https://github.com/google/google-authenticator)
 Operating system | Android, iOS, BlackBerry OS
 Platform | Mobile
 License | Proprietary (earlier versions were under [Apache License](https://en.wikipedia.org/wiki/Apache_License) 2.0)
 Website | [github.com/google/google-authenticator-libpam](https://github.com/google/google-authenticator-libpam)
 
## Technical description

The service provider generates an 80-bit secret key for each user (whereas RFC 4226 §4 requires 128 bits and recommends 160 bits).[39] This is provided as a 16, 26 or 32 character base32 string or as a QR code. The client creates an HMAC-SHA1 using this secret key. The message that is HMAC-ed can be:

the number of 30-second periods having elapsed since the Unix epoch (TOTP); or
the counter that is incremented with each new code (HOTP).
A portion of the HMAC is extracted and converted to a six-digit code.

Pseudocode for one-time password (OTP)

```text
function GoogleAuthenticatorCode(string secret)
      key := base32decode(secret)
      message := floor(current Unix time / 30)
      hash := HMAC-SHA1(key, message)
      offset := last nibble of hash
      truncatedHash := hash[offset..offset+3]  //4 bytes starting at the offset
      Set the first bit of truncatedHash to zero  //remove the most significant bit
      code := truncatedHash mod 1000000
      pad code with 0 from the left until length of code is 6
      return code
```

## Enable Google Authenticator

### Download Google Authenticator

* Android Devices
    * Download from [Google Play](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2) 
    * Or search Google Authenticator in any other markets.
   
* iPhone and iPad
    * Download from [Apple AppStore](http://appstore.com/googleauthenticator)
    
### Enable Google Authenticator on HOT

1. Go to "Security Settings"-"Two Factor Authentication"，click "Enable".
2. Input and verify your payment password.
3. A barcode dialog will be displayed after the verification.
![bar code](/assets/images/p0.png)
4. Open the Google Authenticator app on your phone
![google authenticator](/assets/images/p2.png)
5. Scan the barcode and add it to your list.
![google authenticator](/assets/images/p3.png)
6. Enter the code generated from Google Authenticator on the barcode dialog and click "Bind".

### Close Google Authentication

1. Go to "Security Settings"-"Two Factor Authentication", choose "Close".
2. Input payment password and Google Authenticator code on the unlock dialog.
3. Google Authenticator will be closed after password verification.

### Lost your Google Authenticator

If your phone is lost or the code in the app is removed, you have to send email to `hot-custom@outlook.com` to find it back.
