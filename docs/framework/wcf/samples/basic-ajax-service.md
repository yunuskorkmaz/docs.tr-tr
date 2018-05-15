---
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 0bb8a2b28ea87cb0c22126540f6cdab604ca5120
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="basic-ajax-service"></a><span data-ttu-id="4699f-102">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="4699f-102">Basic AJAX Service</span></span>
<span data-ttu-id="4699f-103">Bu örnek, Windows Communication Foundation (WCF) temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmet (bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz hizmeti) oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4699f-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="4699f-104">Hizmet kullandığı <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği hizmetinin HTTP GET isteklerine yanıt verir ve JavaScript nesne gösterimi (JSON) veri biçimi yanıtlar için kullanmak üzere yapılandırılmış emin olun.</span><span class="sxs-lookup"><span data-stu-id="4699f-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="4699f-105">WCF AJAX desteği ASP.NET AJAX ile kullanmak için en iyisi olan `ScriptManager` denetim.</span><span class="sxs-lookup"><span data-stu-id="4699f-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="4699f-106">WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="4699f-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4699f-107">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4699f-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4699f-108">Aşağıdaki kodda, <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulanan `Add` hizmetinin HTTP GET isteklerine yanıt vermesini sağlamak için işlem.</span><span class="sxs-lookup"><span data-stu-id="4699f-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="4699f-109">Kod GET (bir HTTP GET isteği herhangi bir Web tarayıcısından oluşturabileceğiniz) basitleştirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4699f-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="4699f-110">GET, önbelleğe almayı etkinleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4699f-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="4699f-111">HTTP POST de varsayılandır yokluğu `WebGetAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4699f-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="4699f-112">Örnek .svc dosyasını kullanan <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, hangi ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmetine standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="4699f-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="4699f-113">Uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4699f-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="4699f-114">Bu hizmet adresini anlamına gelir http://localhost/ServiceModelSamples/service.svc, işlem adı dışında hiçbir ek sonek ile.</span><span class="sxs-lookup"><span data-stu-id="4699f-114">This means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="4699f-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> Servisi bir ASP.NET AJAX istemci sayfasından erişilebilir duruma getirmek üzere önceden yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4699f-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="4699f-116">Web.config dosyasında aşağıdaki bölümde, uç nokta için ek yapılandırma değişiklikleri yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4699f-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="4699f-117">Ek bir değişikliğe ihtiyaç olup olmadığını kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4699f-117">It can be removed if no extra changes are required.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4699f-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti için varsayılan veri biçimi XML yerine JSON olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4699f-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="4699f-119">Hizmetini çağırmak için gidin http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 sonra Yukarı kümesi tamamlama ve bu konunun ilerleyen bölümlerinde gösterilen adımlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4699f-119">To invoke the service, navigate to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="4699f-120">Bu test işlev tarafından bir HTTP GET isteği kullanımını etkindir.</span><span class="sxs-lookup"><span data-stu-id="4699f-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="4699f-121">İstemci Web sayfası SimpleAjaxClientPage.aspx kullanıcı işlemi düğmeleri sayfasında birini tıkladığında hizmetini çağırmak için ASP.NET kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="4699f-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="4699f-122">`ScriptManager` Denetimi, bir proxy hizmetinde JavaScript üzerinden erişilebilir yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4699f-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="4699f-123">Yerel proxy örneği ve işlemleri şu JavaScript kodunu kullanarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4699f-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="4699f-124">Hizmet çağrı başarılı olursa, kodu çağırır `onSuccess` işleyicisi ve işlemin sonucunu bir metin kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4699f-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="4699f-125">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4699f-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4699f-126">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4699f-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4699f-127">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4699f-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4699f-128">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4699f-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="4699f-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4699f-129">See Also</span></span>
