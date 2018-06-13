---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 53a0de88d08fbc12cb8861042a50da6503fa5def
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809192"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="4210a-102">Yapılandırma Olmadan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="4210a-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="4210a-103">Bu örnek Windows Communication Foundation (WCF) herhangi bir yapılandırma kullanmadan bir temel ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz hizmeti) oluşturmak için nasıl kullanılacağı gösterilmektedir Ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4210a-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="4210a-104">Hizmet otomatik olarak bir AJAX uç noktayı etkinleştirme .svc dosyasında özel sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4210a-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="4210a-105">WCF AJAX desteği ASP.NET AJAX ile kullanmak için en iyisi olan `ScriptManager` denetim.</span><span class="sxs-lookup"><span data-stu-id="4210a-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="4210a-106">WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [Ajax örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="4210a-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4210a-107">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4210a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4210a-108">Bu örnek AJAX hizmeti kullanarak HTTP POST oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4210a-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="4210a-109">Bölümünde açıklandığı gibi [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmet barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4210a-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="4210a-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> otomatik olarak ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmet.</span><span class="sxs-lookup"><span data-stu-id="4210a-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="4210a-111">Hiçbir yapılandırma değişikliği uç noktasına yapılması gerekiyorsa `<system.ServiceModel>` bölüm tamamen kaldırılabilir hizmeti için Web.config dosyasından.</span><span class="sxs-lookup"><span data-stu-id="4210a-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="4210a-112">Web.config dosyası ConfigFreeClientPage.aspx tarafından kullanılan bazı ASP.NET ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="4210a-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="4210a-113">Durum değildi, tüm Web.config dosyası kaldırılamadı.</span><span class="sxs-lookup"><span data-stu-id="4210a-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4210a-114">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="4210a-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4210a-115">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4210a-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4210a-116">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4210a-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4210a-117">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4210a-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4210a-118">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4210a-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4210a-119">Kurulum yönergeleri gerçekleştirdiğinizden emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4210a-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4210a-120">Çözüm ConfigFreeAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4210a-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4210a-121">Gidin http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (ConfigFreeClientPage.aspx tarayıcıda proje dizininde açık değil).</span><span class="sxs-lookup"><span data-stu-id="4210a-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4210a-122">Lütfen bu örnek çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulaması aynı anda IIS ServiceModelSamples klasörü için etkin olmadığını emin olun.</span><span class="sxs-lookup"><span data-stu-id="4210a-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="4210a-123">Lütfen bu durumda, Windows kimlik doğrulamasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="4210a-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="4210a-124">Örnek çalıştırdıktan sonra Windows kimlik doğrulamasını etkinleştirmek ve "iisreset" çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4210a-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4210a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4210a-125">See Also</span></span>  
 [<span data-ttu-id="4210a-126">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="4210a-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
