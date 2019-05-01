---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: f5ebc952fcc6c2ca4c7272a90dc1929d4b4a0eae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002826"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="29c80-102">Yapılandırma Olmadan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="29c80-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="29c80-103">Bu örnek herhangi bir yapılandırma dosyası olmadan temel ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmet (bir Web tarayıcısı istemcisini JavaScript kodunu kullanarak erişebileceğiniz bir hizmeti) oluşturmak için Windows Communication Foundation (WCF) nasıl yapılacağı açıklanır. Ayarlar.</span><span class="sxs-lookup"><span data-stu-id="29c80-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="29c80-104">Hizmet bir AJAX uç noktası otomatik olarak etkinleştirmeyi .svc dosyasında özel bir sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="29c80-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="29c80-105">WCF AJAX desteği ASP.NET AJAX ile kullanım için optimize `ScriptManager` denetimi.</span><span class="sxs-lookup"><span data-stu-id="29c80-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="29c80-106">ASP.NET AJAX ile WCF kullanan bir örnek için bkz: [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="29c80-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29c80-107">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="29c80-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="29c80-108">Bu örnek, hizmet HTTP POST kullanan AJAX oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29c80-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="29c80-109">Bölümünde anlatıldığı gibi [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneği <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmeti barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29c80-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="29c80-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> otomatik olarak ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmeti.</span><span class="sxs-lookup"><span data-stu-id="29c80-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="29c80-111">Hiçbir yapılandırma değişikliği uç noktasına yapılması gerekiyorsa `<system.ServiceModel>` bölümü tamamen kaldırılabilir hizmeti için Web.config dosyasındaki.</span><span class="sxs-lookup"><span data-stu-id="29c80-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="29c80-112">Web.config dosyası ConfigFreeClientPage.aspx tarafından kullanılan bazı ASP.NET ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="29c80-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="29c80-113">Bu durumda değilse, tüm Web.config dosyası kaldırılamadı.</span><span class="sxs-lookup"><span data-stu-id="29c80-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29c80-114">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="29c80-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="29c80-115">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="29c80-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="29c80-116">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="29c80-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29c80-117">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="29c80-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="29c80-118">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="29c80-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="29c80-119">İçindeki kurulum yönergelerini gerçekleştirdiğinizden emin olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29c80-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="29c80-120">' % S'çözüm ConfigFreeAjaxService.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29c80-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="29c80-121">Gidin `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (ConfigFreeClientPage.aspx tarayıcıda proje dizininden açmayın).</span><span class="sxs-lookup"><span data-stu-id="29c80-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29c80-122">Bu örnek çalışırken, anonim kimlik doğrulaması ve Windows kimlik doğrulaması aynı anda IIS ServiceModelSamples klasöründe etkin olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="29c80-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="29c80-123">Lütfen bu durumda, Windows kimlik doğrulaması devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="29c80-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="29c80-124">Örnek gerçekleştirdikten sonra Windows kimlik doğrulamasını etkinleştirmek ve "iisreset" çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="29c80-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c80-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29c80-125">See also</span></span>

- [<span data-ttu-id="29c80-126">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="29c80-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
