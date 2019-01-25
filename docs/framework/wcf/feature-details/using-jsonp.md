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
# <a name="using-jsonp"></a><span data-ttu-id="af1f1-102">JSONP Kullanma</span><span class="sxs-lookup"><span data-stu-id="af1f1-102">Using JSONP</span></span>

<span data-ttu-id="af1f1-103">JSON doldurma (JSONP), Web tarayıcıları siteler arası betik oluşturma desteği sağlayan bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="af1f1-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="af1f1-104">JSONP geçerli yüklenen belge alınan bir siteden diğerine farklı betikleri yüklemek için Web tarayıcıları yeteneğini geçici olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="af1f1-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="af1f1-105">Kullanıcı tanımlı geri çağırma işlevi adlı bir JSON yükü doldurarak mekanizması aşağıdaki örnekte gösterildiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="af1f1-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="af1f1-106">JSON yükü, yukarıdaki örnekte `{"a" = \\"b\\"}`, bir işlev çağrısında sarmalandıktan `callback`.</span><span class="sxs-lookup"><span data-stu-id="af1f1-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="af1f1-107">Geri çağırma işlevi geçerli bir Web sayfasında zaten tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af1f1-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="af1f1-108">Bir JSONP yanıtın içerik türü `application/javascript`.</span><span class="sxs-lookup"><span data-stu-id="af1f1-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="af1f1-109">JSONP otomatik olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="af1f1-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="af1f1-110">Bunu etkinleştirmek için ayarlanmış `javascriptCallbackEnabled` özniteliğini `true` HTTP standart uç noktaları birinde (<xref:System.ServiceModel.Description.WebHttpEndpoint> veya <xref:System.ServiceModel.Description.WebScriptEndpoint>), aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="af1f1-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="af1f1-111">Geri arama işlevinin adını şu URL'ye gösterildiği gibi bir geri çağırma adında bir sorgu değişkeni belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="af1f1-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="af1f1-112">Hizmet, çağrıldığında, aşağıdakine benzer bir yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="af1f1-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="af1f1-113">Uygulayarak geri çağırma işlevi adı belirtebilirsiniz <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> hizmet sınıfına aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="af1f1-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="af1f1-114">Daha önce gösterilen hizmet için bir istek aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="af1f1-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="af1f1-115">Çağrıldığında, hizmet aşağıdakiler ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="af1f1-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="af1f1-116">HTTP durum kodları</span><span class="sxs-lookup"><span data-stu-id="af1f1-116">HTTP Status Codes</span></span>

<span data-ttu-id="af1f1-117">HTTP durum kodları dışındaki 200 JSONP yanıtları aşağıdaki örnekte gösterildiği gibi sayısal gösterimini HTTP durum kodu ile ikinci bir parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="af1f1-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="af1f1-118">Doğrulamaları</span><span class="sxs-lookup"><span data-stu-id="af1f1-118">Validations</span></span>

<span data-ttu-id="af1f1-119">JSONP'nin etkin olduğunda, aşağıdaki Doğrulamalar gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="af1f1-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="af1f1-120">WCF altyapı bir özel durum oluşturur `javascriptCallback` olan etkin bir geri çağırma sorgu dizesi parametresi istekte mevcut olduğundan ve yanıt biçimi JSON olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="af1f1-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="af1f1-121">İstek geri çağırma sorgu dizesi parametresi içeriyor, ancak bir HTTP GET işlemi değil, geri çağırma parametresi yok sayıldı.</span><span class="sxs-lookup"><span data-stu-id="af1f1-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="af1f1-122">Callback adı ise `null` ya da boş dize yanıt JSONP biçimlendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="af1f1-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="af1f1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af1f1-123">See also</span></span>

- [<span data-ttu-id="af1f1-124">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="af1f1-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
