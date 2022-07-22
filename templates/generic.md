# Generic Template


O modelo genérico é uma mensagem simples estruturada, que contém título, subtítulo, imagem e até três botões. Você pode também especificar um objeto `default_action`, que define um URL que será aberto no WebView do Messenger quando o modelo for tocado.

fields: 
- title 
- subtitle
- image_url
- buttons #0-3 
- default_action

![template-example](https://user-images.githubusercontent.com/75167930/180443053-528243ea-07f1-4996-93a4-f7e733641f20.png)


#### Carousel of Generic Templates

1 - 10 generic templates in elements
```json
"payload": {
  "template_type":"generic",
  "elements":[
    <GENERIC_TEMPLATE>,
    <GENERIC_TEMPLATE>,
    ...
  ]
}
```
![generic-carousel](https://user-images.githubusercontent.com/75167930/180443256-336fa48e-af6a-4875-81aa-7a47395035e4.png)


### Request:

```json
curl -X POST -H "Content-Type: application/json" -d '{
  "recipient":{
    "id":"<PSID>"
  },
  "message":{
    "attachment":{
      "type":"template",
      "payload":{
        "template_type":"generic",
        "elements":[
          {
            "title":"Welcome!",
            "image_url":"https://raw.githubusercontent.com/fbsamples/original-coast-clothing/main/public/styles/male-work.jpg",
            "subtitle":"We have the right hat for everyone.",
            "default_action": {
              "type": "web_url",
              "url": "https://www.originalcoastclothing.com/",
              "webview_height_ratio": "tall",
            },
            "buttons":[
              {
                "type":"web_url",
                "url":"https://www.originalcoastclothing.com/",
                "title":"View Website"
              },{
                "type":"postback",
                "title":"Start Chatting",
                "payload":"DEVELOPER_DEFINED_PAYLOAD"
              }              
            ]      
          }
        ]
      }
    }
  }
}' "https://graph.facebook.com/v2.6/me/messages?access_token=<PAGE_ACCESS_TOKEN>"
```

#### Response
```json
{  
	"recipient_id":  "1254477777772919",  
	"message_id": "AG5Hz2Uq7tuwNEhXfYYKj8mJEM_QPpz5jdCK48PnKAjSdjfipqxqMvK8ma6AC8fplwlqLP_5cgXIbu7I3rBN0P"
}
```

## Práticas recomendadas

✅ Use-o para mensagens com uma hierarquia de informações consistentes (por exemplo, visualizações de produtos ou artigos, previsões meteorológicas).

✅ Use a proporção correta para a sua imagem. Fotos no modelo genérico que não tiverem as dimensões 1,91:1 serão dimensionadas ou recortadas.

❌ Não use se a sua mensagem não tiver informações estruturadas ou exigir hierarquia.

❌ Não use se você precisa que as pessoas sejam capazes de ampliar sua imagem até uma resolução de tela inteira.

### Carrossel

✅ Use um carrossel quando houver uma ordem de prioridade para o seu conteúdo, ou seja, o primeiro item é provavelmente o mais interessante.

✅ Esforce-se para obter consistência. Se um balão tiver uma foto, inclua uma foto em todos os outros.

✅ Minimize o número de modelos genéricos no carrossel. Muitos balões fazem com que as pessoas não se lembrem de todas as opções.

❌ Não misture tipos de conteúdo. Se você incluir um artigo ao lado de uma lista de produtos, sua experiência poderá ficar confusa.

❌ Não use um carrossel quando for importante que as pessoas vejam todo o conteúdo da lista. Elas podem não rolar até o final. Em vez disso, considere um Modelo de lista.

Referência: https://developers.facebook.com/docs/messenger-platform/reference/templates/generic#properties
