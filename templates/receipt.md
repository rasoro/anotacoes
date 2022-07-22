# Receipt Template (Modelo de Recibo)


![receipt-ss](https://user-images.githubusercontent.com/75167930/180443621-e1eb1a2f-0cf4-4a4e-a5f7-a0dd772a29dc.png)


O modelo de recibo permite que você envie uma confirmação de pedido por meio de uma mensagem estruturada. O modelo pode conter o resumo de uma compra, detalhes do pagamento e informações de envio.

## Payload
```json
"payload": {
  "template_type":"receipt",
  "recipient_name":"<CUSTOMER_NAME>",
  "order_number":"<ORDER_NUMBER>",
  "currency":"<CURRENCY_CODE>",
  "payment_method":"<PAYMENT_METHOD_USED>",        
  "order_url":"<LINK_TO_ORDER_SUMMARY>",
  "timestamp":"<ORDER_TIME_AS_POSIX_TIMESTAMP>",         
  "address":{
    "street_1":"<SHIPPING_STREET_ADDRESS>",
    "city":"<SHIPPING_CITY>",
    "postal_code":"<SHIPPING_POSTAL_CODE>",
    "state":"<SHIPPING_STATE>",
    "country":"<SHIPPING_COUNTRY>"
  },
  "summary":{
    "subtotal": <SUBTOTAL_AMOUNT>,
    "shipping_cost": <SHIPPING_AMOUNT>,
    "total_tax": <TAX_AMOUNT>,
    "total_cost": <TOTAL_AMOUNT>
  },
  "adjustments":[
    {
      "name": "<ADJUSTMENT_NAME>",
      "amount": <ADJUSTMENT_AMOUNT>
    },
    ...
  ],
  "elements":[
    {
      "title": "<ITEM_NAME>",
      "subtitle":"<ITEM_DESCRIPTION_OR_DETAILS>",
      "quantity": <QUANTITY>,
      "price": <ITEM_PRICE>,
      "currency": "<CURRENCY_ABBREVIATION",
      "image_url":"<URL_IMAGE_TO_DISPLAY_FOR_ITEM>"
    },
    ...
  ]
}
```

### Request Example

```json
curl -X POST -H "Content-Type: application/json" -d '{
  "recipient":{
    "id":"<PSID>"
  },
  "message":{
    "attachment":{
      "type":"template",
      "payload":{
        "template_type":"receipt",
        "recipient_name":"Stephane Crozatier",
        "order_number":"12345678902",
        "currency":"USD",
        "payment_method":"Visa 2345",        
        "order_url":"http://petersapparel.parseapp.com/order?order_id=123456",
        "timestamp":"1428444852",         
        "address":{
          "street_1":"1 Hacker Way",
          "street_2":"",
          "city":"Menlo Park",
          "postal_code":"94025",
          "state":"CA",
          "country":"US"
        },
        "summary":{
          "subtotal":75.00,
          "shipping_cost":4.95,
          "total_tax":6.19,
          "total_cost":56.14
        },
        "adjustments":[
          {
            "name":"New Customer Discount",
            "amount":20
          },
          {
            "name":"$10 Off Coupon",
            "amount":10
          }
        ],
        "elements":[
          {
            "title":"Classic White T-Shirt",
            "subtitle":"100% Soft and Luxurious Cotton",
            "quantity":2,
            "price":50,
            "currency":"USD",
            "image_url":"http://petersapparel.parseapp.com/img/whiteshirt.png"
          },
          {
            "title":"Classic Gray T-Shirt",
            "subtitle":"100% Soft and Luxurious Cotton",
            "quantity":1,
            "price":25,
            "currency":"USD",
            "image_url":"http://petersapparel.parseapp.com/img/grayshirt.png"
          }
        ]
      }
    }
  }
}' "https://graph.facebook.com/v2.6/me/messages?access_token=<PAGE_ACCESS_TOKEN>"
```
### Response Example

```json
{  
	"recipient_id": "1254477777772919",
	"message_id":  "AG5Hz2Uq7tuwNEhXfYYKj8mJEM_QPpz5jdCK48PnKAjSdjfipqxqMvK8ma6AC8fplwlqLP_5cgXIbu7I3rBN0P"  
}
```

## Práticas recomendadas

✅ Continue a manter as pessoas informadas. Depois de entregar o recibo, envie atualizações oportunas contendo as confirmações de envio e de entrega.

❌ Não use o modelo de recibo para comunicar informações não relacionadas a compras. Ele só deve ser usado para confirmar uma transação anterior.

Referência: https://developers.facebook.com/docs/messenger-platform/reference/templates/receipt
