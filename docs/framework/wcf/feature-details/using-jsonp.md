---
description: 'Hakkında daha fazla bilgi edinin: JSONP kullanma'
title: JSONP Kullanma
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: f4d21670cf468328b8579fa8a9cf2c2e06f09337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632197"
---
# <a name="using-jsonp"></a>JSONP Kullanma

JSON dolgusu (JSONP), Web tarayıcılarında siteler arası betik oluşturma desteğini sağlayan bir mekanizmadır. JSONP, Web tarayıcıları tarafından geçerli yüklenen belgenin alındığı bilgisayardan farklı bir siteden betikleri yükleme yeteneği etrafında tasarlanmıştır. Mekanizma, aşağıdaki örnekte gösterildiği gibi, JSON yükünün Kullanıcı tanımlı geri çağırma işlevi adıyla doldurmasını gerçekleştirerek çalışır.

```javascript
callback({"a" = \\"b\\"});
```

Önceki örnekte JSON yükü, `{"a" = \\"b\\"}` bir işlev çağrısında sarmalanır `callback` . Geri çağırma işlevi, geçerli Web sayfasında zaten tanımlanmış olmalıdır. Bir JSONP yanıtının içerik türü `application/javascript` .

JSONP otomatik olarak etkinleştirilmez. Bunu etkinleştirmek için, `javascriptCallbackEnabled` `true` <xref:System.ServiceModel.Description.WebHttpEndpoint> <xref:System.ServiceModel.Description.WebScriptEndpoint> Aşağıdaki örnekte GÖSTERILDIĞI gibi, özniteliğini http standart uç noktalarından birinde (veya) olarak ayarlayın.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Geri çağırma işlevinin adı, aşağıdaki URL 'de gösterildiği gibi, geri çağırma adlı bir sorgu değişkeninde belirtilebilir.

`http://baseaddress/Service/RestService?callback=functionName`

Çağrıldığında, hizmet aşağıdakine benzer bir yanıt gönderir.

```javascript
functionName({"root":"Something"});
```  

Ayrıca, <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> Aşağıdaki örnekte gösterildiği gibi, hizmet sınıfına uygulayarak geri çağırma işlev adını da belirtebilirsiniz.

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

Çağrıldığında, hizmet aşağıdaki ile yanıt verir.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>HTTP durum kodları

200 dışındaki HTTP durum kodlarına sahip JSONP yanıtları, aşağıdaki örnekte gösterildiği gibi HTTP durum kodunun sayısal gösterimine sahip ikinci bir parametre içerir.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Doğrulamalar

JSONP etkinleştirildiğinde aşağıdaki doğrulamalar gerçekleştirilir:

- WCF altyapısı, etkinleştirilirse bir özel durum oluşturur `javascriptCallback` , istekte bir geri çağırma sorgusu dize parametresi bulunur ve yanıt BIÇIMI JSON olarak ayarlanır.

- İstek geri arama sorgu dizesi parametresini içeriyorsa, ancak işlem bir HTTP GET değilse, geri çağırma parametresi yok sayılır.

- Geri çağırma adı `null` veya boş dize ise yanıt JSONP olarak biçimlendirilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli Genel Bakış](wcf-web-http-programming-model-overview.md)
