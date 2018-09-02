---
title: JSON ve XML ile AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 1beb89c11fccefec24ccbebc3fe30033a646718d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452696"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="332b6-102">JSON ve XML ile AJAX Hizmeti Örneği</span><span class="sxs-lookup"><span data-stu-id="332b6-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="332b6-103">Bu örnek, Windows Communication Foundation (WCF) JavaScript nesne gösterimi (JSON) veya XML veri döndüren bir zaman uyumsuz JavaScript ve XML (AJAX) hizmet oluşturma için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="332b6-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="332b6-104">JavaScript kodu bir Web tarayıcısı istemcisini kullanarak bir AJAX hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="332b6-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="332b6-105">Bu örnek yapılar [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="332b6-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="332b6-106">Diğer AJAX örnekleri farklı olarak, bu örnek, ASP.NET AJAX kullanmaz ve <xref:System.Web.UI.ScriptManager> denetimi.</span><span class="sxs-lookup"><span data-stu-id="332b6-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="332b6-107">Bazı ek yapılandırma ile WCF AJAX Hizmetleri herhangi bir HTML sayfasında JavaScript üzerinden erişilebilir ve bu senaryo burada gösterilir.</span><span class="sxs-lookup"><span data-stu-id="332b6-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="332b6-108">ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [AJAX örnekleri](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="332b6-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
 <span data-ttu-id="332b6-109">Bu örnekte yanıt türü bir işlemin JSON ve XML arasında geçiş yapma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="332b6-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="332b6-110">Bu işlev, mi hizmeti ASP.NET AJAX veya bir HTML/JavaScript istemci sayfası tarafından erişilecek yapılandırılmış bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="332b6-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="332b6-111">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="332b6-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="332b6-112">ASP.NET AJAX istemci kullanımını etkinleştirmek için <xref:System.ServiceModel.Activation.WebServiceHostFactory> (değil <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) .svc dosyasında.</span><span class="sxs-lookup"><span data-stu-id="332b6-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="332b6-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> ekler bir <xref:System.ServiceModel.Description.WebHttpEndpoint> hizmetine standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="332b6-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="332b6-114">Uç nokta, boş bir adresten .svc dosyanın göreli yapılandırılır; Bu hizmet adresini olduğu anlamına gelir http://localhost/ServiceModelSamples/service.svc, işlem adı dışında hiçbir ek sonekleri ile.</span><span class="sxs-lookup"><span data-stu-id="332b6-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="332b6-115">Web.config dosyasında aşağıdaki bölümde, uç nokta için ek yapılandırma değişiklikleri yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="332b6-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="332b6-116">Hiçbir ek değişikliklerin gerekli olup olmadığını kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="332b6-116">It can be removed if no extra changes are needed.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="332b6-117">Varsayılan verilerin biçimlendirilmesi için <xref:System.ServiceModel.Description.WebHttpEndpoint> XML için varsayılan veri biçimi çalışırken olduğu <xref:System.ServiceModel.Description.WebScriptEndpoint> JSON.</span><span class="sxs-lookup"><span data-stu-id="332b6-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="332b6-118">Daha fazla bilgi için [ASP.NET olmadan WCF AJAX hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="332b6-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="332b6-119">Aşağıdaki örnekte iki işlem ile standart bir WCF Hizmeti hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="332b6-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="332b6-120">Her iki işlem gerektiren <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> gövde stilini <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özel öznitelikler `webHttp` davranışı ve JSON/XML veri biçimi anahtarda ilgisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="332b6-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 <span data-ttu-id="332b6-121">Varsayılan olan XML olarak yanıt biçimi işlemi için belirtilen ayarlama [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="332b6-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="332b6-122">Ancak, bunu açıkça alışkanlıktır yanıt biçimi belirtin.</span><span class="sxs-lookup"><span data-stu-id="332b6-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="332b6-123">Başka bir işlem kullandığı `WebInvokeAttribute` özniteliği ve XML yerine JSON yanıtı açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="332b6-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 <span data-ttu-id="332b6-124">Her iki durumda da karmaşık bir tür işlemleri iade Not `MathResult`, standart bir WCF veri anlaşması türü.</span><span class="sxs-lookup"><span data-stu-id="332b6-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>  
  
 <span data-ttu-id="332b6-125">İstemci Web sayfası XmlAjaxClientPage.htm kullanıcı tıkladığında, önceki iki işlemlerden birini çağırır JavaScript kodu içeren **(dönüş JSON'u) hesaplamayı** veya **hesaplamayı (dönüş XML)**  sayfasında düğme.</span><span class="sxs-lookup"><span data-stu-id="332b6-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="332b6-126">Hizmeti çağırmak için kodu, bir JSON gövdesi oluşturur ve HTTP POST kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="332b6-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="332b6-127">İstek, aksine JavaScript'te el ile oluşturulduğunda [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek ve ASP.NET AJAX kullanılarak diğer örnekleri.</span><span class="sxs-lookup"><span data-stu-id="332b6-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 <span data-ttu-id="332b6-128">Hizmet yanıt verdiğinde yanıt herhangi başka bir metin kutusuna sayfasında işlem olmadan görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="332b6-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="332b6-129">Bu, doğrudan kullanılan XML ve JSON veri biçimlerini gözlemleyin olanak sağlamak tanıtım amacıyla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="332b6-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  <span data-ttu-id="332b6-130">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="332b6-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="332b6-131">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="332b6-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="332b6-132">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="332b6-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="332b6-133">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="332b6-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="332b6-134">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="332b6-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="332b6-135">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="332b6-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="332b6-136">' % S'çözüm XmlAjaxService.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="332b6-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="332b6-137">Gidin http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (XmlAjaxClientPage.htm proje dizininden tarayıcıda aç değil).</span><span class="sxs-lookup"><span data-stu-id="332b6-137">Navigate to http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332b6-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="332b6-138">See Also</span></span>  
 [<span data-ttu-id="332b6-139">HTTP POST Kullanan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="332b6-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
