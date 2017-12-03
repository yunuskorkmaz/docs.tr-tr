---
title: JSONP Kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1eedacf6e98d8c6cb71b1cb62b41ce3ef7fcb47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-jsonp"></a><span data-ttu-id="699c7-102">JSONP Kullanma</span><span class="sxs-lookup"><span data-stu-id="699c7-102">Using JSONP</span></span>

<span data-ttu-id="699c7-103">JSON doldurma (JSONP), Web tarayıcıları siteler arası komut dosyası desteği sağlayan bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="699c7-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="699c7-104">JSONP geçerli yüklenen belge öğesinden alınan bir siteden olandan farklı komut dosyaları yükleme özelliğini Web tarayıcılarının çevresinde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="699c7-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="699c7-105">Aşağıdaki örnekte gösterildiği gibi bir kullanıcı tarafından tanımlanan geri çağırma işlevi adıyla JSON yükü doldurma tarafından mekanizması çalışır.</span><span class="sxs-lookup"><span data-stu-id="699c7-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="699c7-106">Önceki örnekte JSON yükü `{"a" = \\"b\\"}`, bir işlev çağrısında Sarmalanan `callback`.</span><span class="sxs-lookup"><span data-stu-id="699c7-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="699c7-107">Geri çağırma işlevi, geçerli Web sayfasındaki zaten tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="699c7-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="699c7-108">Bir JSONP yanıtın içerik türü `application/javascript`.</span><span class="sxs-lookup"><span data-stu-id="699c7-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="699c7-109">JSONP otomatik olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="699c7-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="699c7-110">Etkinleştirmek için ayarlanmış `javascriptCallbackEnabled` özniteliğini `true` HTTP standart uç noktaları birinde (<xref:System.ServiceModel.Description.WebHttpEndpoint> veya <xref:System.ServiceModel.Description.WebScriptEndpoint>), aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="699c7-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="699c7-111">Geri çağırma işlevinin adı aşağıdaki URL'yi gösterildiği gibi geri çağırma adlı bir sorgu değişken belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="699c7-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="699c7-112">Çağrıldığında, hizmet aşağıdakine benzer bir yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="699c7-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="699c7-113">Uygulayarak geri çağırma işlevi adı belirtebilirsiniz <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> aşağıdaki örnekte gösterildiği gibi hizmet sınıfı.</span><span class="sxs-lookup"><span data-stu-id="699c7-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="699c7-114">Daha önce gösterilen hizmeti için bir istek aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="699c7-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="699c7-115">Çağrıldığında, hizmet aşağıdaki ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="699c7-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="699c7-116">HTTP durum kodları</span><span class="sxs-lookup"><span data-stu-id="699c7-116">HTTP Status Codes</span></span>

<span data-ttu-id="699c7-117">HTTP durum kodu 200 dışında JSONP yanıtları HTTP durum kodu sayısal gösterimiyle sahip ikinci bir parametresi aşağıdaki örnekte gösterildiği gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="699c7-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="699c7-118">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="699c7-118">Validations</span></span>

<span data-ttu-id="699c7-119">JSONP etkinleştirilmişse, aşağıdaki Doğrulamalar:</span><span class="sxs-lookup"><span data-stu-id="699c7-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="699c7-120">WCF altyapı bir özel durum döndürürse `javascriptCallback` olduğu etkin bir geri çağırma sorgu dizesi parametresi istekte bulunur ve yanıt biçimi JSON olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="699c7-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="699c7-121">İstek geri çağırma sorgu dizesi parametresi içeriyor, ancak bir HTTP GET işlemi değil, geri çağırma parametresi yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="699c7-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="699c7-122">Geri çağırma adı ise `null` veya boş dize yanıt JSONP biçimlendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="699c7-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="699c7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="699c7-123">See also</span></span>

[<span data-ttu-id="699c7-124">WCF Web HTTP programlama modeli genel bakış</span><span class="sxs-lookup"><span data-stu-id="699c7-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
