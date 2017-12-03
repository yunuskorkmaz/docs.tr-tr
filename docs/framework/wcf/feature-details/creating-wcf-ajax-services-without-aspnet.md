---
title: "ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4ff3e41608c9b879bd64e004fcae5e87599e0b4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="ac7cb-102">ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac7cb-102">Creating WCF AJAX Services without ASP.NET</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ac7cb-103">AJAX Hizmetleri, ASP.NET AJAX gerek kalmadan tüm JavaScript etkin Web sayfasından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-103"> AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="ac7cb-104">Bu konuda gibi oluşturmayı açıklar bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-104">This topic describes how to create such a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="ac7cb-105">Kullanma yönergeleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET AJAX ile bkz [ASP.NET AJAX için WCF hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="ac7cb-105">For instructions on using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="ac7cb-106">Bir oluşturma üç bölümden oluşur bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX hizmeti:</span><span class="sxs-lookup"><span data-stu-id="ac7cb-106">There are three parts to a creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX service:</span></span>  
  
-   <span data-ttu-id="ac7cb-107">AJAX uç noktası oluşturma, tarayıcıdan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
-   <span data-ttu-id="ac7cb-108">Bir AJAX uyumlu hizmet sözleşmesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-108">Creating an AJAX-compatible service contract.</span></span>  
  
-   <span data-ttu-id="ac7cb-109">WCF AJAX Hizmetleri erişme.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="ac7cb-110">AJAX uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac7cb-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="ac7cb-111">AJAX desteğini etkinleştirmek için en temel yolu bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetidir kullanmak için <xref:System.ServiceModel.Activation.WebServiceHostFactory> aşağıdaki örnekteki gibi hizmeti ile ilişkilendirilen .svc dosyasındaki.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-111">The most basic way to enable AJAX support in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="ac7cb-112">Alternatif olarak, bir AJAX uç noktası eklemek için yapılandırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="ac7cb-113">Kullanım <xref:System.ServiceModel.WebHttpBinding> hizmet uç noktası üzerinde ve bu bitiş noktası ile yapılandırma <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kod parçacığında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="ac7cb-114">Çalışan bir örnek için bkz: [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ac7cb-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="ac7cb-115">Bir AJAX uyumlu hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac7cb-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="ac7cb-116">Varsayılan olarak, hizmet sözleşmelerini AJAX bir uç nokta dönüş verileri XML biçiminde üzerinden açık.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="ac7cb-117">Ayrıca, varsayılan olarak hizmet işlemleri aşağıdaki örnekte gösterildiği gibi işlem adından uç noktası adresi dahil URL'ler için HTTP POST istekleri üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="ac7cb-118">Bu işlem bir HTTP POST kullanılarak erişilebilir olduğundan `http://serviceaddress/endpointaddress/GetCities` ve bir XML iletisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="ac7cb-119">Bu temel özelliklerini özelleştirmek için tam Web programlama modelini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="ac7cb-120">Örneğin, kullanabileceğiniz <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi yanıt vereceği HTTP fiili denetlemek veya kullanmak için öznitelikler `UriTemplate` özel URI'ler belirtmek için bu ilgili öznitelikler özelliği.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ac7cb-121">[WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-121"> the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="ac7cb-122">JSON veri biçimi genellikle AJAX Hizmetleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="ac7cb-123">XML yerine JSON döndüren bir işlemi oluşturmak için <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) özelliğine <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="ac7cb-124">[Tek başına JSON serileştirmesi](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konu, JSON olarak nasıl yerleşik .NET türleri ve verileri sözleşme türleri Haritası gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="ac7cb-125">Normalde, JSON isteklerinin ve yanıtlarının yalnızca bir öğe oluşur.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="ac7cb-126">Önceki `GetCities` işlemi, isteği şu deyimi benzer.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="ac7cb-127">Bu istek için yanıt aşağıdaki ifadeyi benzer.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="ac7cb-128">İşlemi fazladan bir parametre alırsa, isteği stili parametrelerinin her ikisini de tek bir JSON nesnesinde sarmalamak için alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="ac7cb-129">Aşağıdaki örnekte bu stil JSON iletisi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="ac7cb-130">Aşağıdaki sözleşme bu iletiyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="ac7cb-131">AJAX hizmetlere erişme</span><span class="sxs-lookup"><span data-stu-id="ac7cb-131">Accessing AJAX Services</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ac7cb-132">AJAX uç noktaları her zaman JSON ve XML isteklerini kabul edin.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-132"> AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="ac7cb-133">HTTP POST istekleri bir içerik türü "application/json" JSON olarak kabul edilir ve XML (örneğin, "text/xml") gösteren içerik türü olan XML olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="ac7cb-134">HTTP GET istekleri URL'de bulunan tüm istek parametrelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="ac7cb-135">Bu uç noktanın HTTP isteği oluşturmak nasıl karar vermek için kullanıcı kadar olur.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="ac7cb-136">Ayrıca, kullanıcının istek gövdesini form JSON oluşturma üzerinde tam denetime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="ac7cb-137">Bir istek JavaScript'ten oluşturma örneği için bkz: [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ac7cb-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
