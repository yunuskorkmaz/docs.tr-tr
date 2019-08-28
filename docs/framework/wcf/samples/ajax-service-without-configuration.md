---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: b3c12801d14c7f6850a985c521c0e3fff92ba8e4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045805"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="b40ef-102">Yapılandırma Olmadan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="b40ef-102">AJAX Service Without Configuration</span></span>

<span data-ttu-id="b40ef-103">Bu örnek, herhangi bir yapılandırma kullanmadan temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) kullanmayı gösterir Ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b40ef-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="b40ef-104">Hizmet, bir AJAX uç noktasını otomatik olarak etkinleştirmek için. svc dosyasında özel söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b40ef-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="b40ef-105">WCF 'de Ajax desteği, `ScriptManager` ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b40ef-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="b40ef-106">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="b40ef-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b40ef-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b40ef-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="b40ef-108">Bu örnek, HTTP POST kullanan AJAX hizmeti üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b40ef-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="b40ef-109">[Temel Ajax hizmet](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğinde açıklandığı gibi, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmetini barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b40ef-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```svc
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="b40ef-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>otomatik olarak hizmetine <xref:System.ServiceModel.Description.WebScriptEndpoint> bir ekler.</span><span class="sxs-lookup"><span data-stu-id="b40ef-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="b40ef-111">Uç noktada hiçbir yapılandırma değişikliği yapılması gerekmiyorsa, `<system.ServiceModel>` Bu bölüm hizmetin Web. config dosyasından tamamen kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b40ef-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="b40ef-112">Web. config dosyası, ConfigFreeClientPage. aspx tarafından kullanılan bazı ASP.NET ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b40ef-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="b40ef-113">Böyle bir durum söz konusu değilse, Web. config dosyasının tamamı kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b40ef-113">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40ef-114">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b40ef-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b40ef-115">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b40ef-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b40ef-116">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="b40ef-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b40ef-117">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b40ef-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b40ef-118">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b40ef-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b40ef-119">[Windows Communication Foundation örnekleri için kurulum yönergelerini bir kerelik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b40ef-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b40ef-120">[Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi ConfigFreeAjaxService. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b40ef-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="b40ef-121">`http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (ConfigFreeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="b40ef-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="b40ef-122">Bu örneği çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulamasının IIS 'deki ServiceModelSamples klasörü için eşzamanlı olarak etkinleştirilmediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b40ef-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="b40ef-123">Bu durumda, lütfen Windows kimlik doğrulamasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b40ef-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="b40ef-124">Örneği çalıştırdığınızda, Windows kimlik doğrulamasını etkinleştirin ve "iisreset" komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b40ef-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="b40ef-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b40ef-125">See also</span></span>

- [<span data-ttu-id="b40ef-126">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="b40ef-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
