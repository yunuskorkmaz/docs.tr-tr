---
title: ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f850d8649f1d67fe916542bfb025afb7cb3f852b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856140"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="3ec82-102">ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ec82-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="3ec82-103">Windows Communication Foundation (WCF) AJAX hizmetlerine, ASP.NET AJAX gerekmeden JavaScript etkin herhangi bir Web sayfasından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3ec82-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="3ec82-104">Bu konuda, böyle bir WCF hizmetinin nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ec82-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="3ec82-105">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili yönergeler için bkz. [ASP.NET AJAX IçIN WCF Hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="3ec82-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="3ec82-106">WCF AJAX Hizmeti oluşturmanın üç bölümü vardır:</span><span class="sxs-lookup"><span data-stu-id="3ec82-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="3ec82-107">Tarayıcıdan erişilebilen bir AJAX uç noktası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3ec82-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="3ec82-108">AJAX uyumlu hizmet sözleşmesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3ec82-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="3ec82-109">WCF AJAX hizmetlerine erişme.</span><span class="sxs-lookup"><span data-stu-id="3ec82-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="3ec82-110">AJAX uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ec82-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="3ec82-111">Bir WCF hizmetinde Ajax desteğini etkinleştirmenin en temel yolu, aşağıdaki örnekte olduğu gibi hizmeti ile <xref:System.ServiceModel.Activation.WebServiceHostFactory> ilişkili. svc dosyasında kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3ec82-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```svc
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="3ec82-112">Alternatif olarak, bir AJAX uç noktası eklemek için yapılandırma da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ec82-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="3ec82-113">Hizmet uç noktasında öğesini kullanın ve bu uç noktayı aşağıdaki kod parçacığında <xref:System.ServiceModel.Description.WebHttpBehavior> gösterildiği gibi ile yapılandırın. <xref:System.ServiceModel.WebHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3ec82-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3ec82-114">Çalışan bir örnek için bkz. [JSON ve XML Ile AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3ec82-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="3ec82-115">AJAX uyumlu hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ec82-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="3ec82-116">Varsayılan olarak, bir AJAX uç noktası üzerinden kullanıma sunulan hizmet sözleşmeleri XML biçimindeki verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ec82-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="3ec82-117">Ayrıca, varsayılan olarak hizmet işlemlerine, aşağıdaki örnekte gösterildiği gibi, uç nokta adresini ve ardından işlem adını içeren URL 'lere HTTP POST istekleri aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3ec82-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="3ec82-118">Bu işleme bir http post `http://serviceaddress/endpointaddress/GetCities` ile erişilebilir ve bir XML iletisi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3ec82-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="3ec82-119">Bu temel yönleri özelleştirmek için tam Web programlama modelini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ec82-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="3ec82-120">Örneğin, <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliklerini kullanarak `UriTemplate` işlemin yanıt verdiği http fiilini denetleyebilir veya özel URI 'leri belirtmek için bu ilgili özniteliklerin özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ec82-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="3ec82-121">Daha fazla bilgi için bkz. [WCF Web http programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="3ec82-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="3ec82-122">JSON veri biçimi genellikle AJAX hizmetlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ec82-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="3ec82-123">XML yerine JSON döndüren bir işlem oluşturmak için <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> ( <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>veya) özelliğini olarak <xref:System.ServiceModel.Web.WebMessageFormat.Json>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3ec82-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="3ec82-124">[Tek BAŞıNA JSON serileştirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konusu, yerleşik .net türlerinin ve veri SÖZLEŞMESI türlerinin JSON ile nasıl eşlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ec82-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="3ec82-125">Normal olarak, JSON istekleri ve yanıtları yalnızca bir öğeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ec82-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="3ec82-126">Önceki `GetCities` işlem için, istek aşağıdaki ifadeye benzer.</span><span class="sxs-lookup"><span data-stu-id="3ec82-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="3ec82-127">Bu isteğin yanıtı aşağıdaki ifadeye benzer.</span><span class="sxs-lookup"><span data-stu-id="3ec82-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="3ec82-128">İşlem ek bir parametre alırsa, her iki parametreyi de tek bir JSON nesnesinde sarmalamak için istek stili sarmalanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ec82-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="3ec82-129">Bu stil JSON iletisine bir örnek aşağıdaki örnekte verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ec82-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="3ec82-130">Aşağıdaki sözleşme bu iletiyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="3ec82-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="3ec82-131">AJAX hizmetlerine erişme</span><span class="sxs-lookup"><span data-stu-id="3ec82-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="3ec82-132">WCF AJAX uç noktaları her zaman hem JSON hem de XML isteklerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="3ec82-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="3ec82-133">İçerik türü "Application/JSON" olan HTTP POST istekleri JSON olarak değerlendirilir ve XML 'yi (örneğin, "text/xml") gösteren içerik türü olanlar XML olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3ec82-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="3ec82-134">HTTP GET istekleri, URL 'deki tüm istek parametrelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3ec82-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="3ec82-135">Bu, uç noktaya HTTP isteğinin nasıl oluşturulacağını belirlemek için kullanıcıya kadar yapılır.</span><span class="sxs-lookup"><span data-stu-id="3ec82-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="3ec82-136">Ayrıca, kullanıcının isteğin gövdesini oluşturan JSON 'u oluşturmak için tam denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="3ec82-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="3ec82-137">JavaScript 'ten bir istek oluşturma örneği için bkz. [JSON ve XML Ile AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3ec82-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
