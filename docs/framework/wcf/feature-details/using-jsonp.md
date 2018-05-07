---
title: JSONP Kullanma
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 55f90c37dc4e94653f2233371a044a2f019b59a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-jsonp"></a>JSONP Kullanma

JSON doldurma (JSONP), Web tarayıcıları siteler arası komut dosyası desteği sağlayan bir mekanizmadır. JSONP geçerli yüklenen belge öğesinden alınan bir siteden olandan farklı komut dosyaları yükleme özelliğini Web tarayıcılarının çevresinde tasarlanmıştır. Aşağıdaki örnekte gösterildiği gibi bir kullanıcı tarafından tanımlanan geri çağırma işlevi adıyla JSON yükü doldurma tarafından mekanizması çalışır.

```javascript
callback({"a" = \\"b\\"});
```

Önceki örnekte JSON yükü `{"a" = \\"b\\"}`, bir işlev çağrısında Sarmalanan `callback`. Geri çağırma işlevi, geçerli Web sayfasındaki zaten tanımlanmış olmalıdır. Bir JSONP yanıtın içerik türü `application/javascript`.

JSONP otomatik olarak etkin değildir. Etkinleştirmek için ayarlanmış `javascriptCallbackEnabled` özniteliğini `true` HTTP standart uç noktaları birinde (<xref:System.ServiceModel.Description.WebHttpEndpoint> veya <xref:System.ServiceModel.Description.WebScriptEndpoint>), aşağıdaki örnekte gösterildiği gibi.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Geri çağırma işlevinin adı aşağıdaki URL'yi gösterildiği gibi geri çağırma adlı bir sorgu değişken belirtilebilir.

`http://baseaddress/Service/RestService?callback=functionName`

Çağrıldığında, hizmet aşağıdakine benzer bir yanıt gönderir.

```javascript
functionName({"root":"Something"});
```  

Uygulayarak geri çağırma işlevi adı belirtebilirsiniz <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> aşağıdaki örnekte gösterildiği gibi hizmet sınıfı.

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

Daha önce gösterilen hizmeti için bir istek aşağıdaki gibi görünür.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Çağrıldığında, hizmet aşağıdaki ile yanıt verir.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>HTTP durum kodları

HTTP durum kodu 200 dışında JSONP yanıtları HTTP durum kodu sayısal gösterimiyle sahip ikinci bir parametresi aşağıdaki örnekte gösterildiği gibi ekleyin.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Doğrulama

JSONP etkinleştirilmişse, aşağıdaki Doğrulamalar:

- WCF altyapı bir özel durum döndürürse `javascriptCallback` olduğu etkin bir geri çağırma sorgu dizesi parametresi istekte bulunur ve yanıt biçimi JSON olarak ayarlanır.

- İstek geri çağırma sorgu dizesi parametresi içeriyor, ancak bir HTTP GET işlemi değil, geri çağırma parametresi yoksayılır.

- Geri çağırma adı ise `null` veya boş dize yanıt JSONP biçimlendirilmemiş.

## <a name="see-also"></a>Ayrıca bkz.

[WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
