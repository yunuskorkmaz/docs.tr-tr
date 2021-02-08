---
description: 'Hakkında daha fazla bilgi edinin: yapılandırma olmadan AJAX Hizmeti'
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 137f0845f042d1919c1cb070c91a473ff81863cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779055"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="3b300-103">Yapılandırma Olmadan AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="3b300-103">AJAX Service Without Configuration</span></span>

<span data-ttu-id="3b300-104">Bu örnekte, herhangi bir yapılandırma ayarı kullanmadan temel bir ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak erişebileceğiniz bir hizmet) oluşturmak için Windows Communication Foundation (WCF) kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b300-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="3b300-105">Hizmet, bir AJAX uç noktasını otomatik olarak etkinleştirmek için. svc dosyasında özel söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b300-105">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="3b300-106">WCF 'de AJAX desteği, ASP.NET AJAX ile denetim aracılığıyla kullanılmak üzere iyileştirilmiştir `ScriptManager` .</span><span class="sxs-lookup"><span data-stu-id="3b300-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="3b300-107">WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="3b300-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3b300-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3b300-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="3b300-109">Bu örnek, HTTP POST kullanan AJAX hizmeti üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b300-109">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="3b300-110">[Temel Ajax hizmet](basic-ajax-service.md) örneğinde açıklandığı gibi, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmetini barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b300-110">As described in the [Basic AJAX Service](basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="3b300-111"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> otomatik olarak hizmetine bir ekler <xref:System.ServiceModel.Description.WebScriptEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="3b300-111"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="3b300-112">Uç noktada hiçbir yapılandırma değişikliği yapılması gerekmiyorsa, `<system.ServiceModel>` bölüm hizmetin Web.config dosyasından tamamen kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b300-112">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="3b300-113">Web.config dosyası, ConfigFreeClientPage. aspx tarafından kullanılan bazı ASP.NET ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3b300-113">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="3b300-114">Böyle bir durum söz konusu değilse, Web.config dosyanın tamamı kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b300-114">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3b300-115">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b300-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3b300-116">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3b300-116">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3b300-117">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3b300-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b300-118">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3b300-118">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3b300-119">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3b300-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3b300-120">[Windows Communication Foundation örnekleri için kurulum yönergelerini bir kerelik kurulum yordamında](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3b300-120">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3b300-121">[Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi ConfigFreeAjaxService. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3b300-121">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="3b300-122">`http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx`(ConfigFreeClientPage. aspx ' i tarayıcıda proje dizininden açmayın) bölümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="3b300-122">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="3b300-123">Bu örneği çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulamasının IIS 'deki ServiceModelSamples klasörü için eşzamanlı olarak etkinleştirilmediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3b300-123">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="3b300-124">Bu durumda, lütfen Windows kimlik doğrulamasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="3b300-124">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="3b300-125">Örneği çalıştırdığınızda, Windows kimlik doğrulamasını etkinleştirin ve "iisreset" komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3b300-125">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="3b300-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b300-126">See also</span></span>

- [<span data-ttu-id="3b300-127">Temel AJAX Hizmeti</span><span class="sxs-lookup"><span data-stu-id="3b300-127">Basic AJAX Service</span></span>](basic-ajax-service.md)
