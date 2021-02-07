---
description: 'Daha fazla bilgi edinin: Temel AJAX Hizmeti'
title: Temel AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 08670c0e87a6f258d29288e2072cd04dd875088a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732728"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="f1851-103">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="f1851-103">Basic AJAX Service</span></span>

<span data-ttu-id="f1851-104">Bu örnek, temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1851-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="f1851-105">Hizmet, <xref:System.ServiceModel.Web.WebGetAttribute> HIZMETIN http get isteklerini yanıtlaması ve yanıtlar için JavaScript nesne gösterimi (JSON) veri biçimini kullanacak şekilde yapılandırıldığından emin olmak için özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1851-105">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>

<span data-ttu-id="f1851-106">WCF 'de AJAX desteği, ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir `ScriptManager` .</span><span class="sxs-lookup"><span data-stu-id="f1851-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="f1851-107">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="f1851-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f1851-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="f1851-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="f1851-109">Aşağıdaki kodda, <xref:System.ServiceModel.Web.WebGetAttribute> `Add` HIZMETIN http get isteklerine yanıt vermesini sağlamak için özniteliği işlemine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f1851-109">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="f1851-110">Kod basitlik için GET kullanır (herhangi bir Web tarayıcısından bir HTTP GET isteği oluşturabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="f1851-110">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="f1851-111">Ayrıca, önbelleğe almayı etkinleştirmek için Al ' i de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1851-111">You can also use GET to enable caching.</span></span> <span data-ttu-id="f1851-112">HTTP POST, öznitelik yokluğunda varsayılandır `WebGetAttribute` .</span><span class="sxs-lookup"><span data-stu-id="f1851-112">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="f1851-113">Örnek. svc dosyası <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmete standart bir uç nokta ekleyen kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1851-113">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="f1851-114">Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f1851-114">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="f1851-115">Bu, hizmetin adresinin, `http://localhost/ServiceModelSamples/service.svc` işlem adından farklı ek sonekler olmadan olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f1851-115">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<span data-ttu-id="f1851-116">, <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmeti bir ASP.NET Ajax istemci sayfasından erişilebilir hale getirmek için önceden yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f1851-116">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="f1851-117">Web.config ' deki aşağıdaki bölüm, uç noktada ek yapılandırma değişiklikleri yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1851-117">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="f1851-118">Ek değişiklik gerekmiyorsa bu, kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1851-118">It can be removed if no extra changes are required.</span></span>

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

<span data-ttu-id="f1851-119">, <xref:System.ServiceModel.Description.WebScriptEndpoint> Hizmetin varsayılan veri biçimini, XML yerıne JSON olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f1851-119">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="f1851-120">Hizmeti çağırmak için, `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` Bu konunun ilerleyen kısımlarında bulunan kurulum ve oluşturma adımlarını tamamladıktan sonra ' a gidin.</span><span class="sxs-lookup"><span data-stu-id="f1851-120">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="f1851-121">Bu test işlevselliği bir HTTP GET isteği kullanılarak etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="f1851-121">This testing functionality is enabled by the use of a HTTP GET request.</span></span>

<span data-ttu-id="f1851-122">Simpleleajaxclientpage. aspx istemci Web sayfası, Kullanıcı sayfadaki işlem düğmelerinden birine her tıkladığında hizmeti çağırmak için ASP.NET kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f1851-122">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="f1851-123">`ScriptManager`Denetim, hizmet üzerinde JavaScript üzerinden erişilebilen bir proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1851-123">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

<span data-ttu-id="f1851-124">Yerel ara sunucu örneği oluşturulur ve işlemler aşağıdaki JavaScript kodu kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f1851-124">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

<span data-ttu-id="f1851-125">Hizmet çağrısı başarılı olursa, kod `onSuccess` işleyiciyi çağırır ve işlemin sonucu bir metin kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f1851-125">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> <span data-ttu-id="f1851-126">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1851-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1851-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f1851-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f1851-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f1851-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1851-129">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f1851-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
