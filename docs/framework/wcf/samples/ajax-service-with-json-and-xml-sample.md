---
title: JSON ve XML ile AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: eadb884667a0b29ef36056f0c3bec4675b7f1b05
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895142"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="b3f60-102">JSON ve XML ile AJAX Hizmeti Örneği</span><span class="sxs-lookup"><span data-stu-id="b3f60-102">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="b3f60-103">Bu örnek, JavaScript Nesne Gösterimi (JSON) veya XML verileri döndüren zaman uyumsuz bir JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="b3f60-104">Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3f60-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="b3f60-105">Bu örnek, [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3f60-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="b3f60-106">Diğer Ajax örneklerinin aksine, bu örnek ASP.NET AJAX ve <xref:System.Web.UI.ScriptManager> denetimini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="b3f60-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="b3f60-107">Bazı ek yapılandırmalar ile, WCF AJAX hizmetlerine JavaScript aracılığıyla herhangi bir HTML sayfasından erişilebilir ve bu senaryo burada gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="b3f60-108">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="b3f60-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="b3f60-109">Bu örnek, bir işlemin yanıt türünün JSON ve XML arasında nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="b3f60-110">Bu işlevsellik, hizmetin ASP.NET AJAX tarafından veya bir HTML/JavaScript istemci sayfası tarafından erişilecek şekilde yapılandırılıp yapılandırılmadığına bakılmaksızın kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="b3f60-111">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3f60-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b3f60-112">Non-ASP.NET AJAX istemcilerinin kullanımını etkinleştirmek için. svc dosyasında ( <xref:System.ServiceModel.Activation.WebServiceHostFactory> Not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3f60-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="b3f60-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory>hizmete standart <xref:System.ServiceModel.Description.WebHttpEndpoint> bir uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="b3f60-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="b3f60-114">Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır; Bu, hizmetin adresinin, işlem adından farklı ek `http://localhost/ServiceModelSamples/service.svc`sonekler olmadan olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

<span data-ttu-id="b3f60-115">Web. config dosyasındaki aşağıdaki bölüm, uç noktada ek yapılandırma değişiklikleri yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="b3f60-116">Ek değişiklik gerekmiyorsa bu, kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-116">It can be removed if no extra changes are needed.</span></span>

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

<span data-ttu-id="b3f60-117">İçin varsayılan veri biçimi <xref:System.ServiceModel.Description.WebScriptEndpoint> XML 'dir,ancakiçinvarsayılanveribiçimiJSONolur.<xref:System.ServiceModel.Description.WebHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="b3f60-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="b3f60-118">Daha fazla bilgi için bkz. [ASP.net olmadan WCF AJAX hizmetleri oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="b3f60-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="b3f60-119">Aşağıdaki örnekteki hizmet, iki işlem içeren standart bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="b3f60-120">Her iki işlem de <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> , `webHttp` davranışa özgü olan <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> JSON/XML veri biçimi anahtarına hiçbir pul bulunmayan ve özniteliklerde gövde stilini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="b3f60-121">İşlemin yanıt biçimi, [ \<Web http >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı için varsayılan ayar olan XML olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="b3f60-122">Ancak, yanıt biçimini açıkça belirtmek iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b3f60-122">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="b3f60-123">Diğer işlem `WebInvokeAttribute` özniteliğini kullanır ve yanıt için XML yerine açıkça JSON belirler.</span><span class="sxs-lookup"><span data-stu-id="b3f60-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="b3f60-124">Her iki durumda da işlemler standart bir WCF veri anlaşması türü olan `MathResult`karmaşık bir tür döndürdüğüne de göz önünde.</span><span class="sxs-lookup"><span data-stu-id="b3f60-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="b3f60-125">XmlAjaxClientPage. htm istemci Web sayfası, Kullanıcı **Hesaplama gerçekleştirme (JSON döndürme)** veya sayfadaki **Hesaplama (dönüş XML)** düğmelerini tıklattığında önceki Iki işlemden birini çağıran JavaScript kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="b3f60-126">Hizmeti çağırmak için kod bir JSON gövdesi oluşturur ve HTTP POST kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="b3f60-127">İstek, [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneği ve ASP.NET Ajax kullanan diğer örneklerin aksine, JavaScript 'te el ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3f60-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

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

<span data-ttu-id="b3f60-128">Hizmet yanıt verdiğinde, yanıt sayfadaki bir metin kutusunda başka işlem yapılmadan görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="b3f60-129">Bu, kullanılan XML ve JSON veri biçimlerini doğrudan gözlemlemeye olanak tanımak için tanıtım amaçlı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b3f60-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="b3f60-130">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3f60-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b3f60-131">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b3f60-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b3f60-132">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="b3f60-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3f60-133">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3f60-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3f60-134">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b3f60-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b3f60-135">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3f60-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b3f60-136">[Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi XmlAjaxService. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3f60-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="b3f60-137">Öğesine `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` gidin (proje dizininden tarayıcıda XmlAjaxClientPage. htm dosyasını açmayın).</span><span class="sxs-lookup"><span data-stu-id="b3f60-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3f60-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3f60-138">See also</span></span>

- [<span data-ttu-id="b3f60-139">HTTP POST Kullanan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="b3f60-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
