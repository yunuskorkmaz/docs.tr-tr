---
title: HTTP POST Kullanan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: f904a26d87a21a931035b45261dbcd970f7d63a1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804114"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="a78b8-102">HTTP POST Kullanan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="a78b8-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="a78b8-103">Bu örnek Windows Communication Foundation (WCF) oluşturmak için nasıl kullanılacağını gösteren bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] HTTP POST kullanan zaman uyumsuz JavaScript ve XML (AJAX) hizmet.</span><span class="sxs-lookup"><span data-stu-id="a78b8-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="a78b8-104">Bir AJAX hizmeti bir Web tarayıcısı istemciden temel JavaScript kodu kullanarak erişebilirsiniz biridir.</span><span class="sxs-lookup"><span data-stu-id="a78b8-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="a78b8-105">Bu örnek derlemeler [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek; iki örnek arasındaki tek fark, HTTP POST HTTP GET yerine kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a78b8-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="a78b8-106">AJAX destek Windows Communication Foundation (WCF) ASP.NET AJAX ile kullanmak için en iyisi olan `ScriptManager` denetim.</span><span class="sxs-lookup"><span data-stu-id="a78b8-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="a78b8-107">WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [Ajax örnekleri](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="a78b8-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a78b8-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a78b8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a78b8-109">Aşağıdaki örnek hizmetinde bir AJAX özgü kod olmadan WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="a78b8-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="a78b8-110">Varsa <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği üzerinde bir işlemi, uygulanan veya <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği uygulanmamış, varsayılan HTTP fiili ("POST") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a78b8-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="a78b8-111">POST istekleri GET istekleri oluşturmak için daha zor olan ancak önbelleğe alınmaz; POST istekleri önbelleğe alma uygun olduğu tüm işlemler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a78b8-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 <span data-ttu-id="a78b8-112">Kullanarak hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="a78b8-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="a78b8-113">GET isteklerinin tersine, tarayıcı POST Hizmetleri'nden çağıramaz.</span><span class="sxs-lookup"><span data-stu-id="a78b8-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="a78b8-114">Örneğin, gezinme http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 POST hizmet beklediği bir hatayla sonuçlanır `n1` ve `n2` ileti gövdesi içinde gönderilmek üzere parametreleri — JSON biçiminde — ve URL içinde değil.</span><span class="sxs-lookup"><span data-stu-id="a78b8-114">For example, navigating to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body—in the JSON format—and not in the URL.</span></span>  
  
 <span data-ttu-id="a78b8-115">İstemci Web sayfası PostAjaxClientPage.aspx kullanıcı işlemi düğmeleri sayfasında birini tıkladığında hizmetini çağırmak için ASP.NET kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="a78b8-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="a78b8-116">Hizmet yanıt olarak aynı şekilde [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) GET isteği ile örnek.</span><span class="sxs-lookup"><span data-stu-id="a78b8-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a78b8-117">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="a78b8-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a78b8-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a78b8-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a78b8-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a78b8-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a78b8-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a78b8-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a78b8-121">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a78b8-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a78b8-122">Kurulum yönergelerini gerçekleştirdiğinizden emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a78b8-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a78b8-123">Çözüm PostAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a78b8-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a78b8-124">Gidin http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (PostAjaxClientPage.aspx proje dizininden tarayıcıda aç değil).</span><span class="sxs-lookup"><span data-stu-id="a78b8-124">Navigate to http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78b8-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a78b8-125">See Also</span></span>
