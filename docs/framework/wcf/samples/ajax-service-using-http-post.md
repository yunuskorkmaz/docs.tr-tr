---
title: HTTP POST Kullanan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c5e5de34573fbfc8a5c6e9607d10881941a9bed5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972017"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="43883-102">HTTP POST Kullanan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="43883-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="43883-103">Bu örnek, HTTP POST kullanan bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="43883-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="43883-104">AJAX Hizmeti, bir Web tarayıcısı istemcisinden temel JavaScript kodu kullanarak erişebileceğiniz bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="43883-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="43883-105">Bu örnek, [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneği üzerinde oluşturulur; iki örnek arasındaki tek fark HTTP GET yerine HTTP POST 'un kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="43883-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="43883-106">Windows Communication Foundation (WCF) ' de Ajax desteği, `ScriptManager` ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="43883-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="43883-107">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="43883-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="43883-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="43883-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="43883-109">Aşağıdaki örnekteki hizmet, AJAX 'a özgü kod içermeyen bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="43883-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="43883-110">Öznitelik bir işleme uygulanmışsa <xref:System.ServiceModel.Web.WebGetAttribute> veya öznitelik uygulanmadığından, varsayılan http fiili ("Post") kullanılır. <xref:System.ServiceModel.Web.WebInvokeAttribute></span><span class="sxs-lookup"><span data-stu-id="43883-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="43883-111">POST isteklerinin oluşturulması, GET isteklerinin daha zordur, ancak önbelleğe alınmaz; önbelleğe almanın uygun olmadığı tüm işlemler için POST istekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="43883-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="43883-112">Temel Ajax hizmet örneğinde olduğu gibi, kullanarak <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>hizmette bir AJAX uç noktası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43883-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="43883-113">GET isteklerinin aksine tarayıcıdan POST hizmetlerini çağıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="43883-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="43883-114">Örneğin, Post hizmeti, `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` `n1` ve `n2` parametrelerinin URL 'de değil JSON biçimindeki ileti gövdesinde gönderilmesini beklediği için, bir hata ile sonuçlara gidiliyor.</span><span class="sxs-lookup"><span data-stu-id="43883-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="43883-115">PostAjaxClientPage. aspx istemci Web sayfası, kullanıcının sayfadaki işlem düğmelerinden birine tıkladığı her seferinde hizmeti çağırmak için ASP.NET kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="43883-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="43883-116">Hizmet, GET isteğiyle birlikte [temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde olduğu gibi yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="43883-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43883-117">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="43883-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="43883-118">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="43883-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="43883-119">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="43883-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43883-120">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="43883-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43883-121">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="43883-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="43883-122">[Windows Communication Foundation örnekleri için kurulum yönergeleri tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="43883-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="43883-123">[Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi, PostAjaxService. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43883-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="43883-124">' A gidin (tarayıcıda, proje dizininden PostAjaxClientPage. aspx ' i açmayın). `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx`</span><span class="sxs-lookup"><span data-stu-id="43883-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
