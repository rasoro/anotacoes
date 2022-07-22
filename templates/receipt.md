# Receipt Template (Modelo de Recibo)


![enter image description here](https://lh3.googleusercontent.com/T4BnlqtqHj12fcjG1IFaqummsonbxYpCeMV4tQ-GqFiSa7EX7ZShuQKrqsmwZmuipgKp8pb-BSacQu_WnsbgsYcdvaItMJ_YTa4nzinBcQ7xSUEw2MXE9lMgPEMZ1HKCQMrM5BDqUdIjYxTIrZDItQSO40y500ObCakfuRdENfJDB5b09sq7O4Fe31Ky0OFSBrdjeFzm9SUHcYXWQIvNV8GbwL5yl22oCb5vxw5W2uVnYCCHctSpGEok8KN_fZJjLUwgfYb_Nb4pkdi5cr8lxun2EsLfv4G4RQTfThx6-bTJUZDWUwPlmzh788dit4o-1UTz9tl_7cHUNr-XNIMNg1mAYlnLsBHT0vZLltnJOOLl66MxyN0vov-GLVTDz5JlwdcBjMHmhrfP18zFqZzHlacTAur5aLP6G-YLUg7fBsRx6UFcdSAF522D3ib4GUpRXm6F9RgSyE2bvW4pXcL2Tmuyq7vQG7tBAs_M8TkKpkpxcPSjxMfAs8XdvAKmiRUP73k4WhKd915yRa0xHnrBxftNN7fqB9jVhjHXhQG6Bmv7cqMPwNHljYsfQaNX_k3VTa4ufVnlM4jfSX2vhmuQmJ1mwaSJ3B6thxiwiUnH5cAzzU4_QenwSVfKLnp2sXauah9TDWojuXUAVGA7KKK1BILmJ0O9uhyMBZhX9at5XO67U7df3-yXpqUCpXPaRwODf693G8mrWwwhwaLfxtWLFUVnPeiFDDXNvMJ4G-1WByYUY8EO11O-KgHgrXElflePWvs1S1qYBYVaI5Cgwu6ZxoiPbxkidYpcN1sH7YdEhvm0ftYr5yeX6Af9U5F_iuGHPlPvh5P1qzHKb_YbGVatagujGnExEHsnCD600T0=w220-h349-no?authuser=1)

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