# Facebook API

In this code we present a URL-based attack in the Facebook graph API. If users are already login into the social network, the attack will directly get their social information such as profile.

```
curl -X POST \
  -F 'access_token=USER_ACCESS_TOKEN' \
  -F 'object=OG_OBJECT_URL' \
https://graph.facebook.com/[User FB ID]/og.likes

```
