---
title: ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185232"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="0b525-102">ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b525-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="0b525-103">Windows Communication Foundation (WCF) AJAX hizmetlerine, JAVAScript özellikli herhangi bir Web sayfasından, ASP.NET AJAX gerektirmeden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0b525-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="0b525-104">Bu konu, böyle bir WCF hizmetinin nasıl oluşturulacak olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b525-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="0b525-105">ASP.NET AJAX ile WCF kullanma ile ilgili talimatlar [için, ASP.NET AJAX için WCF Hizmetleri Oluşturma'ya](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0b525-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="0b525-106">WCF AJAX hizmeti oluşturmanın üç bölümü vardır:</span><span class="sxs-lookup"><span data-stu-id="0b525-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="0b525-107">Tarayıcıdan erişilebilen bir AJAX bitiş noktası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0b525-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="0b525-108">AJAX uyumlu bir hizmet sözleşmesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0b525-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="0b525-109">WCF AJAX hizmetlerine erişim.</span><span class="sxs-lookup"><span data-stu-id="0b525-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="0b525-110">AJAX Bitiş Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b525-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="0b525-111">Bir WCF hizmetinde AJAX desteğini etkinleştirmenin en <xref:System.ServiceModel.Activation.WebServiceHostFactory> temel yolu, aşağıdaki örnekte olduğu gibi hizmetle ilişkili .svc dosyasındakini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0b525-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="0b525-112">Alternatif olarak, bir AJAX bitiş noktası eklemek için yapılandırmayı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b525-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="0b525-113"><xref:System.ServiceModel.WebHttpBinding> Hizmet bitiş noktasını kullanın ve bu bitiş noktasını <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kod parçacığında gösterildiği gibi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="0b525-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="0b525-114">Çalışma örneği [için, JSON ve XML ile AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0b525-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="0b525-115">AJAX Uyumlu Hizmet Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b525-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="0b525-116">Varsayılan olarak, XML formatında bir AJAX uç nokta iade verileri üzerinde maruz kalan hizmet sözleşmeleri.</span><span class="sxs-lookup"><span data-stu-id="0b525-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="0b525-117">Ayrıca, varsayılan olarak hizmet işlemlerine, aşağıdaki örnekte gösterildiği gibi, işlem adının ardından gelen bitiş noktası adresini içeren URL'lere HTTP POST istekleri aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0b525-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="0b525-118">Bu işlem, bir XML `http://serviceaddress/endpointaddress/GetCities` iletisine http post kullanarak erişilebilir ve döndürülebiliyor.</span><span class="sxs-lookup"><span data-stu-id="0b525-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="0b525-119">Bu temel yönleri özelleştirmek için tam Web Programlama Modeli kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b525-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="0b525-120">Örneğin, işlemin yanıtlandığı <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> HTTP fiilini denetlemek veya özel IU'ları `UriTemplate` belirtmek için bu özniteliklerin özelliğini kullanmak için öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b525-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="0b525-121">Daha fazla bilgi için [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="0b525-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="0b525-122">JSON veri formatı genellikle AJAX hizmetlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b525-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="0b525-123">XML yerine JSON döndüren bir işlem <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> oluşturmak <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>için, <xref:System.ServiceModel.Web.WebMessageFormat.Json>(veya) özelliğini .</span><span class="sxs-lookup"><span data-stu-id="0b525-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="0b525-124">[Tek Başına JSON Serileştirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konusu, yerleşik .NET türlerinin ve veri sözleşmesi türlerinin JSON ile nasıl eşleşiş gösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b525-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="0b525-125">Normalde, JSON istekleri ve yanıtları yalnızca bir öğeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0b525-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="0b525-126">Önceki `GetCities` işlem için istek aşağıdaki ifadeye benzer.</span><span class="sxs-lookup"><span data-stu-id="0b525-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="0b525-127">Bu isteğe yanıt aşağıdaki ifadeye benzer.</span><span class="sxs-lookup"><span data-stu-id="0b525-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="0b525-128">İşlem fazladan bir parametre alıyorsa, istek stilinin her iki parametreyi de tek bir JSON nesnesine sarmak için sarılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b525-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="0b525-129">Bu stil JSON iletisinin bir örneği aşağıdaki örnektedir.</span><span class="sxs-lookup"><span data-stu-id="0b525-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="0b525-130">Aşağıdaki sözleşme bu iletiyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0b525-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="0b525-131">AJAX Hizmetlerine Erişim</span><span class="sxs-lookup"><span data-stu-id="0b525-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="0b525-132">WCF AJAX uç noktaları her zaman hem JSON hem de XML isteklerini kabul eylemektedir.</span><span class="sxs-lookup"><span data-stu-id="0b525-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="0b525-133">"Uygulama/json" içerik türüne sahip HTTP POST istekleri JSON olarak kabul edilir ve XML 'yi (örneğin, "text/xml") gösteren içerik türüne sahip olanlar XML olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0b525-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="0b525-134">HTTP GET istekleri, URL'deki tüm istek parametrelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0b525-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="0b525-135">BU HTTP isteğini bitiş noktasına nasıl oluşturacağına karar vermek kullanıcıya kaçıktır.</span><span class="sxs-lookup"><span data-stu-id="0b525-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="0b525-136">Ayrıca, kullanıcı istek gövdesini oluşturan JSON oluşturma üzerinde tam kontrole sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0b525-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="0b525-137">JavaScript'ten istek oluşturma örneği için [JSON ve XML içeren AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0b525-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
