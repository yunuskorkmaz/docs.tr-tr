---
title: JSONP Kullanma
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 622fbdbf2674aea552cfd57f528d7cc5168cfda8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713492"
---
# <a name="using-jsonp"></a>JSONP Kullanma

JSON doldurma (JSONP), Web tarayıcıları siteler arası betik oluşturma desteği sağlayan bir mekanizmadır. JSONP geçerli yüklenen belge alınan bir siteden diğerine farklı betikleri yüklemek için Web tarayıcıları yeteneğini geçici olarak tasarlanmıştır. Kullanıcı tanımlı geri çağırma işlevi adlı bir JSON yükü doldurarak mekanizması aşağıdaki örnekte gösterildiği gibi çalışır.

```javascript
callback({"a" = \\"b\\"});
```

JSON yükü, yukarıdaki örnekte `{"a" = \\"b\\"}`, bir işlev çağrısında sarmalandıktan `callback`. Geri çağırma işlevi geçerli bir Web sayfasında zaten tanımlanmış olmalıdır. Bir JSONP yanıtın içerik türü `application/javascript`.

JSONP otomatik olarak etkin değildir. Bunu etkinleştirmek için ayarlanmış `javascriptCallbackEnabled` özniteliğini `true` HTTP standart uç noktaları birinde (<xref:System.ServiceModel.Description.WebHttpEndpoint> veya <xref:System.ServiceModel.Description.WebScriptEndpoint>), aşağıdaki örnekte gösterildiği gibi.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Geri arama işlevinin adını şu URL'ye gösterildiği gibi bir geri çağırma adında bir sorgu değişkeni belirtilebilir.

`http://baseaddress/Service/RestService?callback=functionName`

Hizmet, çağrıldığında, aşağıdakine benzer bir yanıt gönderir.

```javascript
functionName({"root":"Something"});
```  

Uygulayarak geri çağırma işlevi adı belirtebilirsiniz <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> hizmet sınıfına aşağıdaki örnekte gösterildiği gibi.

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

Daha önce gösterilen hizmet için bir istek aşağıdaki gibi görünür.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Çağrıldığında, hizmet aşağıdakiler ile yanıt verir.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>HTTP durum kodları

HTTP durum kodları dışındaki 200 JSONP yanıtları aşağıdaki örnekte gösterildiği gibi sayısal gösterimini HTTP durum kodu ile ikinci bir parametre içerir.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Doğrulamaları

JSONP'nin etkin olduğunda, aşağıdaki Doğrulamalar gerçekleştirilir:

- WCF altyapı bir özel durum oluşturur `javascriptCallback` olan etkin bir geri çağırma sorgu dizesi parametresi istekte mevcut olduğundan ve yanıt biçimi JSON olarak ayarlanır.

- İstek geri çağırma sorgu dizesi parametresi içeriyor, ancak bir HTTP GET işlemi değil, geri çağırma parametresi yok sayıldı.

- Callback adı ise `null` ya da boş dize yanıt JSONP biçimlendirilmemiş.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
