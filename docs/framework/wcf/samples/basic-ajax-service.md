---
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 8bcfb9a751670d3d1c32de6d8e6f7dc1b84ea30d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002709"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="7363a-102">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="7363a-102">Basic AJAX Service</span></span>
<span data-ttu-id="7363a-103">Bu örnek, Windows Communication Foundation (WCF) temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebileceğiniz bir hizmeti) oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7363a-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="7363a-104">Hizmeti kullandığı <xref:System.ServiceModel.Web.WebGetAttribute> hizmet HTTP GET isteklerine yanıt verir ve yanıtları için JavaScript nesne gösterimi (JSON) veri biçimini kullanacak şekilde yapılandırılmış emin olmak için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7363a-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="7363a-105">WCF AJAX desteği ASP.NET AJAX ile kullanım için optimize `ScriptManager` denetimi.</span><span class="sxs-lookup"><span data-stu-id="7363a-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="7363a-106">ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [AJAX örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="7363a-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7363a-107">Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="7363a-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7363a-108">Aşağıdaki kodda, <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulandığı `Add` hizmet HTTP GET isteklerine yanıt vermesini sağlamak için işlemi.</span><span class="sxs-lookup"><span data-stu-id="7363a-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="7363a-109">Kod Al (herhangi bir Web tarayıcısından HTTP GET isteği oluşturabilirsiniz) kolaylık sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7363a-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="7363a-110">GET, önbelleğe almayı etkinleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7363a-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="7363a-111">HTTP POST, varsayılan olmadığında `WebGetAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7363a-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="7363a-112">Örnek .svc dosyasını kullanan <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, hangi ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmetine standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="7363a-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="7363a-113">Uç nokta, boş bir adresten .svc dosyanın göreli yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7363a-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="7363a-114">Bu hizmet adresini olduğu anlamına gelir `http://localhost/ServiceModelSamples/service.svc`, işlem adı dışında hiçbir ek sonekleri ile.</span><span class="sxs-lookup"><span data-stu-id="7363a-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="7363a-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti bir ASP.NET AJAX istemci sayfasından erişilebilir hale getirmek için önceden yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7363a-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="7363a-116">Web.config dosyasında aşağıdaki bölümde, uç nokta için ek yapılandırma değişiklikleri yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7363a-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="7363a-117">Ek bir değişikliğe ihtiyaç olup olmadığını kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7363a-117">It can be removed if no extra changes are required.</span></span>  
  
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
  
 <span data-ttu-id="7363a-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti için varsayılan veri biçimi XML yerine JSON ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7363a-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="7363a-119">Hizmetini çağırmak için gidin `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` sonra kümesi kurma tamamlanıyor ve bu konunun ilerleyen bölümlerinde gösterilen adımları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7363a-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="7363a-120">Bu test işlevi bir HTTP GET isteği kullanımını tarafından etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7363a-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="7363a-121">İstemci Web sayfası SimpleAjaxClientPage.aspx sayfasında işlemi düğmelerden birine kullanıcı tıkladığında hizmeti çağırmak için ASP.NET kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="7363a-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="7363a-122">`ScriptManager` Denetimi proxy hizmet için JavaScript üzerinden erişilebilir hale getirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7363a-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="7363a-123">Yerel proxy örneği ve aşağıdaki JavaScript kodunu kullanarak işlem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7363a-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="7363a-124">Hizmet çağrısı başarılı olursa, kodu çağıran `onSuccess` işleyicisi ve işlemin sonucunu bir metin kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7363a-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="7363a-125">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="7363a-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7363a-126">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7363a-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7363a-127">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7363a-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7363a-128">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7363a-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
