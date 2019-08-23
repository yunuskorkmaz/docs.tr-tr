---
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 2d3770630df693093b05868f00c409f8245f858b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925244"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="98b1c-102">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="98b1c-102">Basic AJAX Service</span></span>
<span data-ttu-id="98b1c-103">Bu örnek, temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="98b1c-104">Hizmet, hizmetin http <xref:System.ServiceModel.Web.WebGetAttribute> Get isteklerini yanıtlaması ve yanıtlar için JavaScript nesne gösterimi (JSON) veri biçimini kullanacak şekilde yapılandırıldığından emin olmak için özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="98b1c-105">WCF 'de Ajax desteği, `ScriptManager` ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="98b1c-106">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="98b1c-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98b1c-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="98b1c-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="98b1c-108">Aşağıdaki kodda, <xref:System.ServiceModel.Web.WebGetAttribute> hizmetin HTTP GET isteklerine yanıt vermesini sağlamak için `Add` özniteliği işlemine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="98b1c-109">Kod basitlik için GET kullanır (herhangi bir Web tarayıcısından bir HTTP GET isteği oluşturabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="98b1c-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="98b1c-110">Ayrıca, önbelleğe almayı etkinleştirmek için Al ' i de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98b1c-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="98b1c-111">HTTP post, `WebGetAttribute` öznitelik yokluğunda varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="98b1c-112">Örnek. svc dosyası, hizmete <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>standart bir <xref:System.ServiceModel.Description.WebScriptEndpoint> uç nokta ekleyen kullanır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="98b1c-113">Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="98b1c-114">Bu, hizmetin adresinin, işlem adından farklı ek `http://localhost/ServiceModelSamples/service.svc`sonekler olmadan olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="98b1c-115">, <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti bir ASP.NET Ajax istemci sayfasından erişilebilir hale getirmek için önceden yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="98b1c-116">Web. config dosyasındaki aşağıdaki bölüm, uç noktada ek yapılandırma değişiklikleri yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="98b1c-117">Ek değişiklik gerekmiyorsa bu, kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-117">It can be removed if no extra changes are required.</span></span>  
  
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
  
 <span data-ttu-id="98b1c-118">, <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmetin varsayılan veri biçimini, XML yerine JSON olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98b1c-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="98b1c-119">Hizmeti çağırmak için, bu konunun ilerleyen `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` kısımlarında bulunan kurulum ve oluşturma adımlarını tamamladıktan sonra ' a gidin.</span><span class="sxs-lookup"><span data-stu-id="98b1c-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="98b1c-120">Bu test işlevselliği bir HTTP GET isteği kullanılarak etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="98b1c-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="98b1c-121">Simpleleajaxclientpage. aspx istemci Web sayfası, Kullanıcı sayfadaki işlem düğmelerinden birine her tıkladığında hizmeti çağırmak için ASP.NET kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="98b1c-122">`ScriptManager` Denetim, hizmet üzerinde JavaScript üzerinden erişilebilen bir proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="98b1c-123">Yerel ara sunucu örneği oluşturulur ve işlemler aşağıdaki JavaScript kodu kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="98b1c-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="98b1c-124">Hizmet çağrısı başarılı olursa, kod `onSuccess` işleyiciyi çağırır ve işlemin sonucu bir metin kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="98b1c-125">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="98b1c-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98b1c-126">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="98b1c-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98b1c-127">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="98b1c-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98b1c-128">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="98b1c-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
