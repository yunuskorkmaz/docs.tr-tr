---
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: d97ff2d2290d58c0217add306718329a282abbff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192218"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="f11a4-102">Hizmet Hata Ayıklama Davranışı</span><span class="sxs-lookup"><span data-stu-id="f11a4-102">Service Debug Behavior</span></span>
<span data-ttu-id="f11a4-103">Bu örnek, hizmet hata ayıklama davranışı ayarları nasıl yapılandırılabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f11a4-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="f11a4-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="f11a4-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="f11a4-105">Bu örnek, hizmet hata ayıklama davranışı yapılandırma dosyasında açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f11a4-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="f11a4-106">Bunu de kesin kod içinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f11a4-106">It can also be done imperatively in code.</span></span>  
  
 <span data-ttu-id="f11a4-107">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f11a4-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f11a4-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f11a4-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f11a4-109">Sunucu için Web.config dosyasının yardım sayfasına ve aşağıdaki örnekte gösterildiği gibi özel durum işlemeyi etkinleştirmek için hizmet hata ayıklama davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f11a4-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="f11a4-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) hizmet hata ayıklama davranışı özelliklerini değiştirme sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f11a4-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="f11a4-111">Kullanıcı şunları gerçekleştirmek için bu davranışı değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f11a4-111">The user can modify this behavior to achieve the following:</span></span>  
  
-   <span data-ttu-id="f11a4-112">Böylece, özel durum kullanarak bildirilmedi bile uygulama kodu tarafından oluşturulan tüm özel durum döndürülecek hizmetin <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f11a4-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="f11a4-113">Ayarlayarak yapılır `includeExceptionDetailInFaults` için `true`.</span><span class="sxs-lookup"><span data-stu-id="f11a4-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="f11a4-114">Bu ayar, sunucu beklenmeyen bir özel durum burada atma durumlarda hata ayıklama sırasında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f11a4-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f11a4-115">Bir üretim ortamında bu ayarı etkinleştirmek için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="f11a4-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="f11a4-116">Beklenmeyen sunucu özel durum istemci ve bunu ayarlama hedeflenmemiştir bazı bilgiler olabilir `includeExceptionDetailsInFaults` için `true` içinde bilgi sızıntısı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f11a4-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>  
  
-   <span data-ttu-id="f11a4-117">[ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) de etkinleştirmek veya devre dışı yardım sayfasına açmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f11a4-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="f11a4-118">Her bir hizmet, isteğe bağlı olarak hizmet için WSDL almak için uç nokta gibi hizmet hakkındaki bilgileri içeren bir Yardım sayfası kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f11a4-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="f11a4-119">Bu ayarlayarak etkinleştirilebilir `httpHelpPageEnabled` için `true`.</span><span class="sxs-lookup"><span data-stu-id="f11a4-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="f11a4-120">Bu hizmetin taban adresi için bir GET isteği için döndürülecek yardım sayfasına sağlar.</span><span class="sxs-lookup"><span data-stu-id="f11a4-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="f11a4-121">Başka bir özniteliğini ayarlayarak bu adresi değişebilir `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="f11a4-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="f11a4-122">Bu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f11a4-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="f11a4-123">Bu ayarlayarak yapılabilir `httpsHelpPageEnabled` ve `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="f11a4-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>  
  
 <span data-ttu-id="f11a4-124">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f11a4-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f11a4-125">İlk üç işlemleri (ekleme, çıkarma ve Çarp) başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f11a4-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="f11a4-126">Son işlem ("bölme") bir bölme sıfır özel durum ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f11a4-126">The last operation ("divide") fails with a division by zero exception.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f11a4-127">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f11a4-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f11a4-128">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f11a4-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f11a4-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f11a4-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f11a4-130">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f11a4-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f11a4-131">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="f11a4-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f11a4-132">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f11a4-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f11a4-133">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f11a4-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f11a4-134">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f11a4-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
