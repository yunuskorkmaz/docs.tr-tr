---
title: JSONP Kullanma
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 82290319b5d8b58708f0b2ebf40522ee76127b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594965"
---
# <a name="using-jsonp"></a><span data-ttu-id="34a24-102">JSONP Kullanma</span><span class="sxs-lookup"><span data-stu-id="34a24-102">Using JSONP</span></span>

<span data-ttu-id="34a24-103">JSON dolgusu (JSONP), Web tarayıcılarında siteler arası betik oluşturma desteğini sağlayan bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="34a24-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="34a24-104">JSONP, Web tarayıcıları tarafından geçerli yüklenen belgenin alındığı bilgisayardan farklı bir siteden betikleri yükleme yeteneği etrafında tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="34a24-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="34a24-105">Mekanizma, aşağıdaki örnekte gösterildiği gibi, JSON yükünün Kullanıcı tanımlı geri çağırma işlevi adıyla doldurmasını gerçekleştirerek çalışır.</span><span class="sxs-lookup"><span data-stu-id="34a24-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="34a24-106">Önceki örnekte JSON yükü, `{"a" = \\"b\\"}` bir işlev çağrısında sarmalanır `callback` .</span><span class="sxs-lookup"><span data-stu-id="34a24-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="34a24-107">Geri çağırma işlevi, geçerli Web sayfasında zaten tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34a24-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="34a24-108">Bir JSONP yanıtının içerik türü `application/javascript` .</span><span class="sxs-lookup"><span data-stu-id="34a24-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="34a24-109">JSONP otomatik olarak etkinleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="34a24-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="34a24-110">Bunu etkinleştirmek için, `javascriptCallbackEnabled` `true` <xref:System.ServiceModel.Description.WebHttpEndpoint> <xref:System.ServiceModel.Description.WebScriptEndpoint> Aşağıdaki örnekte GÖSTERILDIĞI gibi, özniteliğini http standart uç noktalarından birinde (veya) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="34a24-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="34a24-111">Geri çağırma işlevinin adı, aşağıdaki URL 'de gösterildiği gibi, geri çağırma adlı bir sorgu değişkeninde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="34a24-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="34a24-112">Çağrıldığında, hizmet aşağıdakine benzer bir yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="34a24-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="34a24-113">Ayrıca, <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> Aşağıdaki örnekte gösterildiği gibi, hizmet sınıfına uygulayarak geri çağırma işlev adını da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34a24-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="34a24-114">Daha önce gösterilen hizmet için bir istek aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="34a24-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="34a24-115">Çağrıldığında, hizmet aşağıdaki ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="34a24-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="34a24-116">HTTP durum kodları</span><span class="sxs-lookup"><span data-stu-id="34a24-116">HTTP Status Codes</span></span>

<span data-ttu-id="34a24-117">200 dışındaki HTTP durum kodlarına sahip JSONP yanıtları, aşağıdaki örnekte gösterildiği gibi HTTP durum kodunun sayısal gösterimine sahip ikinci bir parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="34a24-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="34a24-118">Doğrulamalar</span><span class="sxs-lookup"><span data-stu-id="34a24-118">Validations</span></span>

<span data-ttu-id="34a24-119">JSONP etkinleştirildiğinde aşağıdaki doğrulamalar gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="34a24-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="34a24-120">WCF altyapısı, etkinleştirilirse bir özel durum oluşturur `javascriptCallback` , istekte bir geri çağırma sorgusu dize parametresi bulunur ve yanıt BIÇIMI JSON olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="34a24-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="34a24-121">İstek geri arama sorgu dizesi parametresini içeriyorsa, ancak işlem bir HTTP GET değilse, geri çağırma parametresi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="34a24-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="34a24-122">Geri çağırma adı `null` veya boş dize ise yanıt JSONP olarak biçimlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="34a24-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="34a24-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34a24-123">See also</span></span>

- [<span data-ttu-id="34a24-124">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="34a24-124">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
