# Product template

![tp](https://user-images.githubusercontent.com/75167930/180443413-a1384b8f-b0b6-457c-a2db-cb4f016eacd1.png)

O modelo de produto é uma mensagem estruturada que pode ser usada para renderizar produtos que foram carregados em um [catálogo](https://developers.facebook.com/micro_site/url/?click_from_context_menu=true&country=BR&destination=https://www.facebook.com/business/help/1275400645914358&event_type=click&last_nav_impression_id=0SoVbADtuy4ZEcGd0&max_percent_page_viewed=100&max_viewport_height_px=980&max_viewport_width_px=1920&orig_http_referrer=https://developers.facebook.com/docs/messenger-platform/send-messages/template/product&orig_request_uri=https://developers.facebook.com/ajax/docs/nav/?path1=messenger-platform&path2=send-messages&path3=template&path4=product&region=latam&scrolled=true&session_id=1iBA7t48UpCUU9Rjh&site=developers). Os detalhes do produto (imagem, título, preço) serão automaticamente retirados do catálogo de produtos.

### template payload:
```
"payload": {
  "template_type":"product",
  "elements":[
     {
        "id":<PRODUCT_ID>
     },
   ]
}
  ```

product_ids podem ser obtidos via [Catalog API](https://developers.facebook.com/micro_site/url/?click_from_context_menu=true&country=BR&destination=https://developers.facebook.com/docs/marketing-api/catalog/&event_type=click&last_nav_impression_id=08ZJB8pWS8h1Uk9wH&max_percent_page_viewed=49&max_viewport_height_px=980&max_viewport_width_px=1920&orig_http_referrer=https://developers.facebook.com/docs/messenger-platform/send-messages/template/product&orig_request_uri=https://developers.facebook.com/ajax/docs/nav/?path1=messenger-platform&path2=send-messages&path3=template&path4=product&region=latam&scrolled=true&session_id=1iBA7t48UpCUU9Rjh&site=developers) ou via [Facebook Commerce Manager](https://developers.facebook.com/micro_site/url/?click_from_context_menu=true&country=BR&destination=https://www.facebook.com/business/help/2371372636254534?id=533228987210412&event_type=click&last_nav_impression_id=0SoVbADtuy4ZEcGd0&max_percent_page_viewed=100&max_viewport_height_px=980&max_viewport_width_px=1920&orig_http_referrer=https://developers.facebook.com/docs/messenger-platform/send-messages/template/product&orig_request_uri=https://developers.facebook.com/ajax/docs/nav/?path1=messenger-platform&path2=send-messages&path3=template&path4=product&region=latam&scrolled=true&session_id=1iBA7t48UpCUU9Rjh&site=developers). O modelo de produto é compatível apenas com product_ids pertencentes à mesma página.

### Sending a Carousel of Product Templates

```json
"payload": {
  "template_type":"product",
  "elements":[
    {
        "id":<PRODUCT_ID_1>
    },
    {
        "id":<PRODUCT_ID_2>
    }
    ...
  ]
}
```

### Example Request

```json
curl -X POST -H "Content-Type: application/json" -d '{
  "recipient":{
    "id":"<PSID>"
  },
  "message":{
    "attachment":{
      "type":"template",
        "payload": {
          "template_type": "product",
          "elements": [
            {
              "id": "<PRODUCT_ID_1>"
            },
            {
              "id": "<PRODUCT_ID_2>"
            }
         ]
      }
    }
  }
}' "https://graph.facebook.com/v8.0/me/messages?access_token=<PAGE_ACCESS_TOKEN>"
```

Referência: https://developers.facebook.com/docs/messenger-platform/send-messages/template/product
