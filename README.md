Simple App


## Local variables

```
APPLE_APP_ID = "Apple app id"
APPLE_ID = "Apple id"
APPLE_PASSWORD = "App specific password generated under apple id account"
APPLE_TEAM_ID = "Apple developer team id"
APPLE_CERT_IDENTITY = "Developer ID Application: ... (...)"
```


## Github Actions

Open Xcode, go into the signing certificates modal, and export the Developer ID Application certificate (called `APPLE_SIGNING_CERTIFICATE_BASE64` from here on) we’ve been referring to in the last guide. To export the certificate, choose a secure password and remember it for later. To retrieve the base64-encoded certificate representation after exporting, run

```
base64 -i APPLE_SIGNING_CERTIFICATE_BASE64.p12 | pbcopy
```

To import the code signing certificate to GitHub Actions, you should end up with two secrets: `APPLE_SIGNING_CERTIFICATE_BASE64` and `APPLE_SIGNING_CERTIFICATE_PASSWORD`. To create a temporary Keychain instance, configure a random `KEYCHAIN_PASSWORD`.

Configure secrets for GithubActions
```
APPLE_SIGNING_CERTIFICATE_BASE64 =
APPLE_SIGNING_CERTIFICATE_PASSWORD =  
KEYCHAIN_PASSWORD = 
```





## Create icns Icon

```
  # Prepare a 1024 x 1024 image and rename it to icon.png.

  sips -z 16 16 icon.png --out icons.iconset/icon_16x16.png
  sips -z 32 32 icon.png --out icons.iconset/icon_16x16@2x.png
  sips -z 32 32 icon.png --out icons.iconset/icon_32x32.png
  sips -z 64 64 icon.png --out icons.iconset/icon_32x32@2x.png
  sips -z 64 64 icon.png --out icons.iconset/icon_64x64.png
  sips -z 128 128 icon.png --out icons.iconset/icon_64x64@2x.png
  sips -z 128 128 icon.png --out icons.iconset/icon_128x128.png
  sips -z 256 256 icon.png --out icons.iconset/icon_128x128@2x.png
  sips -z 256 256 icon.png --out icons.iconset/icon_256x256.png
  sips -z 512 512 icon.png --out icons.iconset/icon_256x256@2x.png
  sips -z 512 512 icon.png --out icons.iconset/icon_512x512.png
  sips -z 1024 1024 icon.png --out icons.iconset/icon_512x512@2x.png
  
  iconutil -c icns icons.iconset -o icons.icns
```