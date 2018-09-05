---
title: HTTP POST Kullanan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c102d9d403cefb1bf3d4ab75859a81172895c2e0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659546"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="fbe2f-102">HTTP POST Kullanan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="fbe2f-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="fbe2f-103">Bu örnek oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösteren bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] HTTP POST kullanan zaman uyumsuz JavaScript ve XML (AJAX) hizmet.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="fbe2f-104">Bir AJAX temel JavaScript kodunu bir Web tarayıcısı istemcisini kullanarak erişebileceğiniz bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="fbe2f-105">Bu örnek yapılar [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek; iki örnek arasındaki tek fark, HTTP POST HTTP GET yerine kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="fbe2f-106">AJAX desteği Windows Communication Foundation (WCF) ASP.NET AJAX ile kullanım için optimize `ScriptManager` denetimi.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="fbe2f-107">ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [Ajax örnekleri](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="fbe2f-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbe2f-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fbe2f-109">Aşağıdaki örnekte bir WCF Hizmeti AJAX özgü kod olmadan hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="fbe2f-110">Varsa <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelik, bir işlem üzerinde uygulanan veya <xref:System.ServiceModel.Web.WebGetAttribute> öznitelik uygulanmadı, varsayılan HTTP fiili ("POST") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="fbe2f-111">GET isteği oluşturmak için POST istekleri daha zor olan, ancak önbelleğe alınmaz. POST istekleri önbelleğe alma uygun olduğu tüm işlemler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 <span data-ttu-id="fbe2f-112">Kullanarak, hizmette bir AJAX uç noktası oluşturma <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, yalnızca temel AJAX hizmeti örneği olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="fbe2f-113">GET istekleri tarayıcıdan GÖNDERİSİNE Hizmetleri çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="fbe2f-114">Örneğin, giderek http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 POST hizmet beklediği için hata sonuçları `n1` ve `n2` ileti gövdesinde gönderilecek parametreleri — JSON biçiminde — ve URL.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-114">For example, navigating to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body—in the JSON format—and not in the URL.</span></span>  
  
 <span data-ttu-id="fbe2f-115">İstemci Web sayfası PostAjaxClientPage.aspx sayfasında işlemi düğmelerden birine kullanıcı tıkladığında hizmeti çağırmak için ASP.NET kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="fbe2f-116">Hizmet yanıt olarak aynı şekilde [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) GET isteğiyle örnek.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fbe2f-117">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fbe2f-118">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fbe2f-119">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fbe2f-120">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fbe2f-121">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="fbe2f-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fbe2f-122">Kurulum yönergelerini gerçekleştirdiğinizden emin olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbe2f-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fbe2f-123">' % S'çözüm PostAjaxService.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fbe2f-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fbe2f-124">Gidin http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (PostAjaxClientPage.aspx proje dizininden tarayıcıda aç değil).</span><span class="sxs-lookup"><span data-stu-id="fbe2f-124">Navigate to http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe2f-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-125">See Also</span></span>
