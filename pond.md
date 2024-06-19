# Ferramentas de PLN da AWS

## 1. Amazon Comprehend

### Descrição
Amazon Comprehend é um serviço de pln que usa machine learning para encontrar insights em um texto. Ele consegue identificar a linguagem do texto, encontrar palavras ou frases principais, lugares, pessoas, marcas ou eventos, e entender o sentimento (positivo, negativo, neutro) no texto, etc.

### Exemplo de Aplicação
Enviando uma requisição HTTP para analisar o sentimento de um comentário.

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "X-Amz-Target: Comprehend_20171127.DetectSentiment" \
  -H "X-Amz-Date: 20210617T000000Z" \ 
  -H "Authorization: AWS4-HMAC-SHA256 Credential=YOUR_ACCESS_KEY/20210617/us-east-1/comprehend/aws4_request, SignedHeaders=content-type;host;x-amz-date;x-amz-target, Signature=YOUR_SIGNATURE" \
  --data '{ "Text": "I love this!", "LanguageCode": "en" }' \
  https://comprehend.us-east-1.amazonaws.com
```

### Resultado: 
```bash
{
    "Sentiment": "POSITIVE",
    "SentimentScore": {
        "Positive": 0.982,
        "Negative": 0.001,
        "Neutral": 0.017,
        "Mixed": 0.000
    }
```

## 2. Amazon Translate 

### Descrição
Amazon Translate é um serviço de tradução automática que oferece traduções em vários idiomas.

### Exemplo:
Enviando uma requisição HTTP para traduzir texto.
```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "X-Amz-Target: AWSShineFrontendService_20170701.TranslateText" \
  -H "X-Amz-Date: 20210617T000000Z" \
  -H "Authorization: AWS4-HMAC-SHA256 Credential=YOUR_ACCESS_KEY/20210617/us-east-1/translate/aws4_request, SignedHeaders=content-type;host;x-amz-date;x-amz-target, Signature=YOUR_SIGNATURE" \
  --data '{ "Text": "Hello, world!", "SourceLanguageCode": "en", "TargetLanguageCode": "es" }' \
  https://translate.us-east-1.amazonaws.com
```

### Resultado:
```bash
{
    "TranslatedText": "¡Hola, mundo!",
    "SourceLanguageCode": "en",
    "TargetLanguageCode": "es"
}
```

## 3. Amazon Lex:

### Descrição:
Amazon Lex é um serviço que serve para criar interfaces de conversação em aplicações usando áudio e texto. Ele tem funcionalidades de reconhecimento de fala automática  e de compreensão de linguagem natural

### Exemplo: 
Criando um chatbot que responde a cumprimentos
```bash
{
  "name": "OrderFlowers",
  "description": "Bot to order flowers on any occasion",
  "intents": 
    {
      "name": "GreetingIntent",
      "sampleUtterances": ["Hello", "Hi", "Hey"],
      "fulfillmentActivity": {
        "type": "ReturnIntent"
      }
    }
  ,
  "locale": "en-US",
  "childDirected": false

```

### Resultado:
```bash
{
  "dialogState": "Fulfilled",
  "intentName": "GreetingIntent",
  "message": "Hi, how can I help you?",
  "slots": {}
}
```
