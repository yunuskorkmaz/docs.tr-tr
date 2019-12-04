---
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 6a0a1c5d9f9741da978c633d35ea1e39664bed5b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716300"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="9044c-102">Hizmet Hata Ayıklama Davranışı</span><span class="sxs-lookup"><span data-stu-id="9044c-102">Service Debug Behavior</span></span>

<span data-ttu-id="9044c-103">Bu örnek, hizmet hata ayıklama davranışı ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9044c-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="9044c-104">Örnek, `ICalculator` hizmet sözleşmesini uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="9044c-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="9044c-105">Bu örnek, yapılandırma dosyasında hizmet hata ayıklama davranışını açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9044c-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="9044c-106">Ayrıca, kod içinde imperatively de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="9044c-106">It can also be done imperatively in code.</span></span>

<span data-ttu-id="9044c-107">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="9044c-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="9044c-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="9044c-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="9044c-109">Sunucu için Web. config dosyası, aşağıdaki örnekte gösterildiği gibi yardım sayfası ve özel durum işlemeyi etkinleştirmek için hizmet hata ayıklama davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9044c-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>

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

<span data-ttu-id="9044c-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) , hizmet hata ayıklama davranışı özelliklerinin değiştirilmesini sağlayan yapılandırma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="9044c-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="9044c-111">Kullanıcı bu davranışı değiştirerek aşağıdakileri elde edebilir:</span><span class="sxs-lookup"><span data-stu-id="9044c-111">The user can modify this behavior to achieve the following:</span></span>

- <span data-ttu-id="9044c-112">Bu, özel durum <xref:System.ServiceModel.FaultContractAttribute>kullanılarak bildirilmemiş olsa bile, hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9044c-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="9044c-113">`includeExceptionDetailInFaults` `true`olarak ayarlanarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="9044c-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="9044c-114">Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="9044c-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9044c-115">Bu ayarı bir üretim ortamında açmak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="9044c-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="9044c-116">Beklenmeyen bir sunucu özel durumu, istemciye yönelik amaçlı olmayan bazı bilgiler içerebilir ve `includeExceptionDetailsInFaults` `true` ayarı bir bilgi sızıntısına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9044c-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>

- <span data-ttu-id="9044c-117">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) , kullanıcının yardım sayfasını etkinleştirmesine veya devre dışı bırakmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9044c-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="9044c-118">Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir.</span><span class="sxs-lookup"><span data-stu-id="9044c-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="9044c-119">Bu, `httpHelpPageEnabled` `true`ayarlanarak etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9044c-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="9044c-120">Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9044c-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="9044c-121">Başka bir öznitelik `httpHelpPageUrl`ayarlayarak bu adresi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9044c-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="9044c-122">Bunu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9044c-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="9044c-123">Bu, `httpsHelpPageEnabled` ve `httpsHelpPageUrl`ayarlanarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="9044c-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>

<span data-ttu-id="9044c-124">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9044c-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9044c-125">İlk üç işlem (ekleme, çıkarma ve çarpma) başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9044c-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="9044c-126">Son işlem ("Böl"), sıfıra bölme özel durumuyla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9044c-126">The last operation ("divide") fails with a division by zero exception.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9044c-127">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9044c-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="9044c-128">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9044c-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="9044c-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9044c-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="9044c-130">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9044c-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9044c-131">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9044c-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9044c-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9044c-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9044c-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="9044c-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9044c-134">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9044c-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
