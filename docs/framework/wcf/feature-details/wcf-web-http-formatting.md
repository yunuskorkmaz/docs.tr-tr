---
title: WCF Web HTTP biçimlendirme
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: f3d3a2d992f234c690f3fb87514b700a6596a5fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935479"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="f5916-102">WCF Web HTTP biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="f5916-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="f5916-103">WCF Web HTTP programlama modeli yanıtına döndürmek bir hizmet işlemi için en iyi biçimi dinamik olarak belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f5916-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="f5916-104">Uygun bir biçim belirlemek için iki yöntem desteklenir: otomatik ve açık.</span><span class="sxs-lookup"><span data-stu-id="f5916-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="f5916-105">Otomatik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="f5916-105">Automatic formatting</span></span>  
 <span data-ttu-id="f5916-106">Etkin olduğunda, otomatik biçimlendirme yanıtta döndürülecek en iyi biçimde seçer.</span><span class="sxs-lookup"><span data-stu-id="f5916-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="f5916-107">Aşağıdaki sırayla denetleyerek, en iyi biçimi belirler:</span><span class="sxs-lookup"><span data-stu-id="f5916-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="f5916-108">Medya türleri istek iletisinin Accept üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="f5916-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="f5916-109">İstek iletisi content-type.</span><span class="sxs-lookup"><span data-stu-id="f5916-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="f5916-110">Varsayılan biçimi ayarlama işlemi.</span><span class="sxs-lookup"><span data-stu-id="f5916-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="f5916-111">İçinde WebHttpBehavior ayarı varsayılan biçimi.</span><span class="sxs-lookup"><span data-stu-id="f5916-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="f5916-112">İsteğine bir Accept üst bilgisi içeriyorsa, Windows Communication Foundation (WCF) altyapısı onu destekleyen bir türü arar.</span><span class="sxs-lookup"><span data-stu-id="f5916-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="f5916-113">Varsa `Accept` medya türlerinden öncelikleri üstbilgisini belirtir, bunların tümü kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f5916-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="f5916-114">Hiçbir uygun biçimde bulunursa `Accept` üst bilgi, istek iletisinin içerik türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5916-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="f5916-115">Uygun içerik türü belirtilirse, ayarlama işlemi için varsayılan biçimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5916-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="f5916-116">Varsayılan biçimi ile ayarlanır `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="f5916-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="f5916-117">Hiçbir varsayılan biçimi işlemi, değerini belirttiyseniz, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> özelliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5916-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="f5916-118">Otomatik biçimlendirme dayanır <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f5916-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="f5916-119">Bu özelliği ayarlandığında `true`, WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="f5916-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="f5916-120">Otomatik Biçim Seçimi varsayılan olarak devre dışıdır için geriye dönük uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="f5916-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="f5916-121">Otomatik Biçim Seçimi program aracılığıyla veya yapılandırma yoluyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5916-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="f5916-122">Aşağıdaki örnek kodda Otomatik Biçim Seçimi etkinleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5916-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract     
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();        
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="f5916-123">Otomatik biçimlendirme yapılandırma aracılığıyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5916-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="f5916-124">Ayarlayabileceğiniz <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliği doğrudan üzerinde <xref:System.ServiceModel.Description.WebHttpBehavior> veya bu adı kullanıyor <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="f5916-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="f5916-125">Aşağıdaki örnek otomatik biçim seçimi üzerinde nasıl etkinleştirileceğini gösterir <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f5916-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f5916-126">Aşağıdaki örnek, Otomatik Biçim Seçimi kullanarak etkinleştirmek gösterilmektedir <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="f5916-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="f5916-127">Explicit biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="f5916-127">Explicit formatting</span></span>  
 <span data-ttu-id="f5916-128">Adından da anlaşılacağı gibi açık biçimlendirmede Geliştirici işlem kodu içinde kullanmak için en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="f5916-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="f5916-129">En iyi biçimi XML veya JSON ise Geliştirici ayarlar <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> ya da <xref:System.ServiceModel.Web.WebMessageFormat.Xml> veya <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="f5916-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="f5916-130">Varsa <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> özelliği açıkça ayarlanmamışsa, ardından işlem varsayılan biçimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5916-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="f5916-131">Aşağıdaki örnek, biçim sorgu dizesi parametresi için kullanılacak biçimi denetler.</span><span class="sxs-lookup"><span data-stu-id="f5916-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="f5916-132">Belirtilen değilse, işlemin ayarlar kullanılarak Biçimlendirilecek <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5916-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="f5916-133">XML veya JSON dışında biçimleri için destek gerekiyorsa, dönüş türüne sahip olmasını işleminizi tanımlama <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="f5916-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="f5916-134">İşlem kod içinde kullanmak ve oluşturmak için uygun biçimde belirlemek bir <xref:System.ServiceModel.Channels.Message> aşağıdaki yöntemlerden birini kullanarak nesne:</span><span class="sxs-lookup"><span data-stu-id="f5916-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="f5916-135">Bu yöntemlerin her biri, içerik alır ve bir ileti ile uygun biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5916-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="f5916-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Yöntemi tercih azalan dosyasındaki istemci tarafından tercih edilen biçimler listesini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5916-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="f5916-137">Aşağıdaki örnek nasıl kullanılacağını gösterir `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` biçimini kullanın ve ardından kullanan belirlemek için uygun bir yanıt iletisi oluşturmak için yanıt yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5916-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5916-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5916-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="f5916-139">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="f5916-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="f5916-140">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="f5916-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="f5916-141">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5916-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="f5916-142">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="f5916-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
