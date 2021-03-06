# Avatar Generator

Generates default avatars from a given string (such as username). This is mainly for an usage in web apps, but you can olso use it to populate LDAP "jpegPhoto" field, for instance.

This is largely inspired by [Richard O'Dwyer's randomavatar](https://github.com/richardasaurus/randomavatar).

![](examples/photo3.png "")
![](examples/photo2.png "")
![](examples/photo1.png "")

## Installation

    pip install avatar-generator

## Example in a Flask app

    from avatar_generator import Avatar
    from flask import make_response

    @app.route("/photo.png")
    def photo():
        avatar = Avatar.generate(128, "example@sysnove.fr", "PNG")
        headers = { 'Content-Type': 'image/png' }
        return make_response(avatar, 200, headers)

## Generating static images

    python generate.py
    cd out
    aws s3 cp . s3://<bucketname>/avatar/default/ --recursive --acl=public-read --cache-control='max-age=31536000, public'

## Licence

This code is under [WTFPL](https://en.wikipedia.org/wiki/WTFPL). Just do what the fuck you want with it.
