---
title: "Hizmet Hata Ayıklama Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 007ce7eeae6022255ad1b31921e14e0518d72bee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="service-debug-behavior"></a><span data-ttu-id="9db70-102">Hizmet Hata Ayıklama Davranışı</span><span class="sxs-lookup"><span data-stu-id="9db70-102">Service Debug Behavior</span></span>
<span data-ttu-id="9db70-103">Bu örnek, hizmet hata ayıklama davranışı ayarları nasıl yapılandırılabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="9db70-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="9db70-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme.</span><span class="sxs-lookup"><span data-stu-id="9db70-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="9db70-105">Bu örnek, hizmet hata ayıklama davranışı yapılandırma dosyasında açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9db70-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="9db70-106">Bu da imperatively kodda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="9db70-106">It can also be done imperatively in code.</span></span>  
  
 <span data-ttu-id="9db70-107">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="9db70-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9db70-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="9db70-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9db70-109">Sunucu için Web.config dosyasının Yardım sayfası ve aşağıdaki örnekte gösterildiği gibi özel durum işleme etkinleştirmek için hizmet hata ayıklama davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9db70-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="9db70-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) hizmet hata ayıklama davranışı özelliklerini değiştirme sağlayan yapılandırma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="9db70-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="9db70-111">Kullanıcı aşağıdakileri gerçekleştirmek için bu davranışı değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9db70-111">The user can modify this behavior to achieve the following:</span></span>  
  
-   <span data-ttu-id="9db70-112">Özel durum kullanarak bildirilmedi olsa bile uygulama kodu tarafından oluşturulan özel durumları döndürülecek hizmetin böylece <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9db70-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="9db70-113">Ayarlayarak yapılır `includeExceptionDetailInFaults` için `true`.</span><span class="sxs-lookup"><span data-stu-id="9db70-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="9db70-114">Bu ayar, sunucu beklenmeyen bir özel durum burada atma durumlarda hata ayıklama sırasında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9db70-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9db70-115">Bir üretim ortamında bu ayarı etkinleştirmek için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="9db70-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="9db70-116">Beklenmeyen sunucu özel durum istemci ve bunu ayarı amaçlanmamıştır bazı bilgiler olabilir `includeExceptionDetailsInFaults` için `true` içinde bilgi sızıntısı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9db70-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>  
  
-   <span data-ttu-id="9db70-117">[ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) Ayrıca, kullanıcının etkinleştirme veya devre dışı yardım sayfasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9db70-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="9db70-118">Her hizmet, isteğe bağlı olarak hizmet için WSDL almak için uç nokta da dahil olmak üzere hizmeti hakkında bilgi içeren bir Yardım sayfası getirebilir.</span><span class="sxs-lookup"><span data-stu-id="9db70-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="9db70-119">Bu ayarlayarak etkinleştirilebilir `httpHelpPageEnabled` için `true`.</span><span class="sxs-lookup"><span data-stu-id="9db70-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="9db70-120">Bu hizmetin taban adresi için bir GET isteğine döndürülecek Yardım sayfası sağlar.</span><span class="sxs-lookup"><span data-stu-id="9db70-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="9db70-121">Başka bir öznitelik ayarlayarak bu adresi değiştirebilirsiniz `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="9db70-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="9db70-122">Bu HTTP yerine HTTPS kullanılarak güvenli hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="9db70-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="9db70-123">Bu ayar yapılabilir `httpsHelpPageEnabled` ve `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="9db70-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>  
  
 <span data-ttu-id="9db70-124">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9db70-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9db70-125">İlk üç işlemleri (eklemek, çıkarmak ve çarpma) başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9db70-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="9db70-126">Son işlem ("bölme") ile bölme sıfır bir özel durum nedeniyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9db70-126">The last operation ("divide") fails with a division by zero exception.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9db70-127">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="9db70-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9db70-128">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9db70-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9db70-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9db70-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9db70-130">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9db70-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9db70-131">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9db70-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9db70-132">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9db70-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9db70-133">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9db70-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9db70-134">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9db70-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a><span data-ttu-id="9db70-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9db70-135">See Also</span></span>
