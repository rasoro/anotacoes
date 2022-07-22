# Product template

![enter image description here](https://lh3.googleusercontent.com/RAOBB-mWEyMIj0uKs0TqxMASjjs0jw4C3ejPmOhX7t7d_04-nJOtwbZMrqgLKPYlbP40fTOCcpSbb1D-H3QYSDxGSVurDl93LNCy0qzSBOPkPcbRtKJODCMLsza9Cp0LJJUuBsYxF7do5MptokzvBAJMoB6N77len2NyNmzI-hYpyTtebgw9mvOye8-vWx5MdiBHS30UJ2gN3rLEdvObIh4kb-19kk8xEUoAmUyGiSpDFZRuZXuWsnswIp-rpNaYUyqbeUHpH5R6At_c6b6LsKVoXxNts9hInp5_CY7vv4YdnjI8tDg2oJ0iKp49d2wTMyvqgn2OaonsYvE-SPWBxb_G2jb5a72kbQ4MgYv5Z8P-OJeYlp_r8aQmN-Op3sE0WvN-EFJLPqdPwWbCGBLcT5x8hjaUYmWdIek24ft2lgjKKvVEsyp5vHi1xlkQY_yhgHWgpngx-sEx2qXn_Rky7xnScBbAcR1ioblCnq1WZRQMBjiNinjoKFoZGbNUbf2ImY0wTSIMJVyPbU7JLthC3JWWUjU_Xp2bufVdVj0I3IboRArpabvSGRRLC_yKSt7Fud2PzHnr67B4Yx41kp0Ru9YWqxK947fJcNmZ3kwid8kvr2jz34Dyl0Sk5UO2DlUKFAzPrh8A2GYv_bH5yb96xRz9SBhpIO_IPrsTLRLqYa2NB4o27Lc6-FCDwBO3krrAZGHY40usmSul7O3QSU0sPpr-YtO20nPynda_i2IW7AABllhsYB_5IDDYjKVV60--xnrm2NE-0-bUYE3Fz_dyObTi5e6Iyepg5w4b1bXOPg_ax5OAZsFlQ8ydOFikMl1_-MhgrfzX5AuV1GohyfAD7s3BZNUiHHKnbdlFod4=w213-h245-no?authuser=1)

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