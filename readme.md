# Tipos de mensagem de template
- [Generic](https://developers.facebook.com/docs/messenger-platform/reference/templates/generic)
- [Button](https://developers.facebook.com/docs/messenger-platform/reference/template/button)
- [Receipt](https://developers.facebook.com/docs/messenger-platform/reference/template/receipt)
- [Media](https://developers.facebook.com/docs/messenger-platform/reference/template/media)
- [Product](https://developers.facebook.com/docs/messenger-platform/reference/template/product)
- [Customer Feedback](https://developers.facebook.com/docs/messenger-platform/reference/templates/customer-feedback-template)

### Envio de uma mensagem de template

URL:
```
https://graph.facebook.com/`v14.0`/me/messages?access_token=<PAGE_ACCESS_TOKEN>
```

Body:
```json
{
  "recipient":{s
    "id":"<PSID>"
  },
  "message":{
    "attachment":{
      "type":"template",
      "payload":{
        "template_type":"<TEMPLATE_TYPE>",//(generic, button,receipt, media, product, customer feedback
        ...
      }
    }
  }
}
```

### montando uma mensagem de template

![result](https://user-images.githubusercontent.com/75167930/180442707-4db3851a-4723-4df9-a71a-116669c64d65.png)

