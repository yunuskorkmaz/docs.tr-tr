---
title: ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857213"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="89eac-102">ASP.NET Olmadan WCF AJAX Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="89eac-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="89eac-103">Windows Communication Foundation (WCF) AJAX Hizmetleri, ASP.NET AJAX gerek kalmadan, tüm JavaScript etkin Web sayfasından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="89eac-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="89eac-104">Bu konuda bu tür bir WCF hizmeti oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="89eac-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="89eac-105">ASP.NET AJAX ile WCF kullanma ile ilgili yönergeler için bkz: [ASP.NET AJAX için WCF hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="89eac-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="89eac-106">Bir WCF AJAX hizmeti oluşturmanın üç bölümü vardır:</span><span class="sxs-lookup"><span data-stu-id="89eac-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="89eac-107">Bir AJAX uç noktası oluşturma bir tarayıcıdan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="89eac-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="89eac-108">Bir AJAX uyumlu hizmet anlaşması oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="89eac-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="89eac-109">AJAX WCF hizmetlerine erişme.</span><span class="sxs-lookup"><span data-stu-id="89eac-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="89eac-110">Bir AJAX uç noktası oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="89eac-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="89eac-111">Bir WCF hizmetinde AJAX desteğini etkinleştirmek için en temel yolu <xref:System.ServiceModel.Activation.WebServiceHostFactory> .svc dosyasında aşağıdaki örnekteki gibi bir hizmet ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="89eac-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="89eac-112">Alternatif olarak, bir AJAX uç noktası eklemek için yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89eac-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="89eac-113">Kullanım <xref:System.ServiceModel.WebHttpBinding> hizmet uç noktasında ve uç noktasına yapılandırma <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kod parçacığında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="89eac-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="89eac-114">Çalışan bir örnek için bkz. [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="89eac-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="89eac-115">Bir AJAX uyumlu hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="89eac-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="89eac-116">Varsayılan olarak, hizmet sözleşmelerini AJAX bir uç nokta dönüş verileri XML biçiminde üzerinden kullanıma.</span><span class="sxs-lookup"><span data-stu-id="89eac-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="89eac-117">Ayrıca, hizmet işlemleri varsayılan olarak aşağıdaki örnekte gösterildiği gibi işlem adından önce gelen uç nokta adresini içeren URL'leri için HTTP POST istekleri aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="89eac-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="89eac-118">Bu işlem, bir HTTP POST kullanılarak erişilebilir `http://serviceaddress/endpointaddress/GetCities` ve bir XML iletisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="89eac-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="89eac-119">Tam Web programlama modeli temel özellikleri özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89eac-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="89eac-120">Örneğin, kullanabilirsiniz <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi yanıt vereceği HTTP fiili denetlemek veya öznitelikleri `UriTemplate` özelliği özel bir URI'leri belirtmek için bu ilgili özniteliklerin.</span><span class="sxs-lookup"><span data-stu-id="89eac-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="89eac-121">Daha fazla bilgi için [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) konu.</span><span class="sxs-lookup"><span data-stu-id="89eac-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="89eac-122">JSON veri biçimi genellikle AJAX hizmetlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89eac-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="89eac-123">XML yerine JSON döndüren bir işlem oluşturmak için <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) özelliğini <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="89eac-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="89eac-124">[Tek başına JSON serileştirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) konu, JSON için nasıl yerleşik .NET türleri ve veri anlaşması türleri Haritası gösterir.</span><span class="sxs-lookup"><span data-stu-id="89eac-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="89eac-125">Normalde, yalnızca bir öğesi olan JSON isteklerini ve yanıtlarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="89eac-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="89eac-126">Önceki `GetCities` işlemi, istek aşağıdaki deyimi benzer.</span><span class="sxs-lookup"><span data-stu-id="89eac-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="89eac-127">Bu isteğin yanıtını aşağıdaki deyimi benzer.</span><span class="sxs-lookup"><span data-stu-id="89eac-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="89eac-128">İşlem ek bir parametre alırsa, tek bir JSON nesnesinde hem parametreler sarmalamak için istek stili alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89eac-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="89eac-129">Aşağıdaki örnekte bu stil JSON iletisi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="89eac-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="89eac-130">Şu sözleşme bu iletiyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="89eac-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="89eac-131">AJAX hizmetlerine erişme</span><span class="sxs-lookup"><span data-stu-id="89eac-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="89eac-132">WCF AJAX uç noktaları her zaman hem JSON hem de XML isteklerini kabul etmek.</span><span class="sxs-lookup"><span data-stu-id="89eac-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="89eac-133">HTTP POST istekleri bir content-type "application/json" JSON olarak kabul edilir ve bu XML (örneğin, "metin/xml") gösteren içerik türü ile XML olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="89eac-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="89eac-134">HTTP GET istekleri URL içinde tüm istek parametrelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="89eac-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="89eac-135">Bu uç nokta için HTTP isteği oluşturmak nasıl karar vermek için kullanıcı en fazla olur.</span><span class="sxs-lookup"><span data-stu-id="89eac-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="89eac-136">Ayrıca, kullanıcının istek gövdesini form JSON oluşturmak üzerinde tam denetime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="89eac-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="89eac-137">JavaScript'ten bir isteği oluşturma örneği için bkz: [JSON ve XML ile AJAX hizmeti](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="89eac-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
