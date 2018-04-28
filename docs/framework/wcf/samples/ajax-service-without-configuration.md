---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae16dc38c5508eac4a94d464e818f0b97d3b9e3b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="65e67-102">Yapılandırma Olmadan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="65e67-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="65e67-103">Bu örnek nasıl kullanılacağı ortaya [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] herhangi bir yapılandırma ayarı kullanmadan bir temel ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz hizmeti) oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="65e67-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="65e67-104">Hizmet otomatik olarak bir AJAX uç noktayı etkinleştirme .svc dosyasında özel sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="65e67-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="65e67-105">AJAX Destek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET AJAX ile kullanım için optimize edilmiştir `ScriptManager` denetim.</span><span class="sxs-lookup"><span data-stu-id="65e67-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="65e67-106">Kullanarak bir örnek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET AJAX ile bkz [Ajax örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="65e67-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65e67-107">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="65e67-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="65e67-108">Bu örnek AJAX hizmeti kullanarak HTTP POST oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65e67-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="65e67-109">Bölümünde açıklandığı gibi [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmet barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65e67-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="65e67-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> otomatik olarak ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmet.</span><span class="sxs-lookup"><span data-stu-id="65e67-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="65e67-111">Hiçbir yapılandırma değişikliği uç noktasına yapılması gerekiyorsa `<system.ServiceModel>` bölüm tamamen kaldırılabilir hizmeti için Web.config dosyasından.</span><span class="sxs-lookup"><span data-stu-id="65e67-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="65e67-112">Web.config dosyası ConfigFreeClientPage.aspx tarafından kullanılan bazı ASP.NET ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="65e67-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="65e67-113">Durum değildi, tüm Web.config dosyası kaldırılamadı.</span><span class="sxs-lookup"><span data-stu-id="65e67-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="65e67-114">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="65e67-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="65e67-115">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="65e67-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="65e67-116">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="65e67-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65e67-117">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="65e67-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="65e67-118">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="65e67-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="65e67-119">Kurulum yönergeleri gerçekleştirdiğinizden emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="65e67-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="65e67-120">Çözüm ConfigFreeAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="65e67-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="65e67-121">Gidin http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (ConfigFreeClientPage.aspx tarayıcıda proje dizininde açık değil).</span><span class="sxs-lookup"><span data-stu-id="65e67-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65e67-122">Lütfen bu örnek çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulaması aynı anda IIS ServiceModelSamples klasörü için etkin olmadığını emin olun.</span><span class="sxs-lookup"><span data-stu-id="65e67-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="65e67-123">Lütfen bu durumda, Windows kimlik doğrulamasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="65e67-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="65e67-124">Örnek çalıştırdıktan sonra Windows kimlik doğrulamasını etkinleştirmek ve "iisreset" çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="65e67-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e67-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65e67-125">See Also</span></span>  
 [<span data-ttu-id="65e67-126">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="65e67-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
