# Generic Template


O modelo genérico é uma mensagem simples estruturada, que contém título, subtítulo, imagem e até três botões. Você pode também especificar um objeto `default_action`, que define um URL que será aberto no WebView do Messenger quando o modelo for tocado.

fields: 
- title 
- subtitle
- image_url
- buttons #0-3 
- default_action

![generic-template-payload](https://lh3.googleusercontent.com/IK3PtsJ9kWT89JbuFhdmlWp5FbEAzwlRkKYjGsuOleRe36n9dcWY9FNc0bJ6lRuIMJ7M03JJisE3XH-037sUdDLdmDFg9drIugEysUnnR7RSpkNECXS2puyBQqjRrjKfyLMBmd7nxs7mHSDO1Oskd7cK9MHHpABnkderVS2U8mqDq6ZzDn9GVM5UwTMxyFXQQJpjIITne8mkwBQumhhbTS5v19_kKnTbHecss1gnejEUjNrjn1uNKQfnDuL-tPNmN2donCMGxeHJ13lEuguLqNYM-lZrFsW3VV1IaIWU9oFLylG1hV3jYPChHUp8lldIdSoiGslrkg3PcwgauN3xv2ZdSUMn9XGnPnDqHXYEoOgY-VWCZlhQpNa7mNQFP1O0I3l4uZlcnoqmw2RFYy9CBgNcgLxQWqmL-FGtfpCfznbicDmdYrIodV4QcjlxtazXZE6W17EX449zA0V-KK44KYq6qCSnkGBBgqgYvsMdmQKn4soiq9m2iuTnAd98cIITOfM3wkYKfZa1C98oje-Ir65_02cO7jmoE1y6FQl6JsDuiHBDE9NJMmPpRFkOKNZGhGTgyQ71nPIdpYirZ-XzYXJmFM9m6lD4pW3N9f5xShBwccqIc3WDuB6FjfQIrOjmJn2WmMKhbpvOKzghERpfHb8bj6OdhtcuH4g3vhTb-Ab7gq6-eS3dOie4OhPK-o_p4FK-5LTs_hsKVNeHMbWtJ0T699NrYoev9Ho518_75jJfEmr9YQYW75nUMC20o3KGl3Ea4vlLY0YHapf6tTlJshW-vAROiPVaJ4PUIytuIQQcif-3u21nwyLeANcj6O4RXNw_YzwuBXANsFhwqHMcVWOJYTZ8ug0YP0QOrgM=w871-h501-no?authuser=1)

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
![enter image description here](https://lh3.googleusercontent.com/o2lTnnuTQIcumXgeYnDkr9C-DElyMMgr3ypIs4ZidjD6qG3WxgtTdUMKjDp9cMqpRrOWRSLqIgQsNN94_TWa1sWwVS9ukqVEevqBkzZt7g5vyuris7k_GbxPQB2HE4koEeYpxPYATvrDjEIrJejnU76ZMT8tvs8nMNtrcVTlzKd-3cRIsQz6LSCgZ1i_qJ-H0xLCXs44rz5EtcNWIr9JexqMOHleg1fzQd_1ZKp4mUUGxtmB1XS8iA4FFbmgJkLKt8xXV_dK6yXyvonOxtgdM0loQBMIHCDwm0dHAQ-uPgAb0n6ysVsHTNf7YyuA6XokyE1eRtGxu1j6HPweiXX31Db_fp-wj-rFwLyX4CyysHkJem7bbnh7NRiBTxITSrezNEiFEgrjxFNzQPvCECAEUWr-YU4oue3hYxzv0s_BY0WzCxEevInZ3_G4xUAI2CoUapZPbgZHVyQNfZ-XkqGb64OCP7Q2xwBK6q0iiDvPrkh9gSiQqbKNwG2Lq7siaeUVmjPwwQcmmmqgUHW7L_BkBAZY0bAKrwzCTa440QukldE_JAAVygWXzYrr2MWonYTtAMpCuR9pvYeNfVuUiJDzElBOwdvp_mGwEpc23MYaLwnAkG09YerKA1pe14w_HkHTau5e-IhugHks2hqe5LP-jqA21T3PwQaQWDwlPUs28TZh-CQ06b7dcN12gnI0dvA5-k43PmRZg2Zkh4F8sBmiNncpPOgYVw4muG_Ub_laMUm0VOEihsTuICCT98s_otcO8_mgQUC9H2q4gKwOPqxEv7IA2t7-gD_kD5lsmC-pwxD7Q3P4U4uBfDq7WKWTWunGnSEaJL-WNyDx5qjjIjSg80KREdJV6DHh9AON-BE=w586-h239-no?authuser=1)

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