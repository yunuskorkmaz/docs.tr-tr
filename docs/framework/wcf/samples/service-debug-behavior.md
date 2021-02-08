---
description: 'Daha fazla bilgi edinin: hizmet hata ayıklama davranışı'
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 3aae4a4cca53fce50bff8ec02896e748f430166f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793109"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="4c770-103">Hizmet Hata Ayıklama Davranışı</span><span class="sxs-lookup"><span data-stu-id="4c770-103">Service Debug Behavior</span></span>

<span data-ttu-id="4c770-104">Bu örnek, hizmet hata ayıklama davranışı ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c770-104">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="4c770-105">Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="4c770-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="4c770-106">Bu örnek, yapılandırma dosyasında hizmet hata ayıklama davranışını açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4c770-106">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="4c770-107">Ayrıca, kod içinde imperatively de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c770-107">It can also be done imperatively in code.</span></span>

<span data-ttu-id="4c770-108">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="4c770-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="4c770-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="4c770-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="4c770-110">Sunucu için Web.config dosyası, aşağıdaki örnekte gösterildiği gibi yardım sayfası ve özel durum işlemeyi etkinleştirmek için hizmet hata ayıklama davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4c770-110">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>

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

<span data-ttu-id="4c770-111">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) , hizmet hata ayıklama davranışı özelliklerinin değiştirilmesini sağlayan yapılandırma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="4c770-111">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="4c770-112">Kullanıcı bu davranışı değiştirerek aşağıdakileri elde edebilir:</span><span class="sxs-lookup"><span data-stu-id="4c770-112">The user can modify this behavior to achieve the following:</span></span>

- <span data-ttu-id="4c770-113">Bu, özel durum kullanılarak bildirilmemiş olsa bile hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar <xref:System.ServiceModel.FaultContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4c770-113">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="4c770-114">Ayarıyla yapılır `includeExceptionDetailInFaults` `true` .</span><span class="sxs-lookup"><span data-stu-id="4c770-114">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="4c770-115">Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c770-115">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="4c770-116">Bu ayarı bir üretim ortamında açmak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="4c770-116">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="4c770-117">Beklenmeyen bir sunucu özel durumu, istemciye yönelik amaçlı olmayan bazı bilgiler içerebilir ve bu nedenle ayarı `includeExceptionDetailsInFaults` `true` bilgi sızıntısına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c770-117">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>

- <span data-ttu-id="4c770-118">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)Ayrıca, bir kullanıcının yardım sayfasını etkinleştirmesine veya devre dışı bırakmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4c770-118">The [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="4c770-119">Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir.</span><span class="sxs-lookup"><span data-stu-id="4c770-119">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="4c770-120">Bu, ayarına göre etkinleştirilebilir `httpHelpPageEnabled` `true` .</span><span class="sxs-lookup"><span data-stu-id="4c770-120">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="4c770-121">Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c770-121">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="4c770-122">Başka bir öznitelik ayarlayarak bu adresi değiştirebilirsiniz `httpHelpPageUrl` .</span><span class="sxs-lookup"><span data-stu-id="4c770-122">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="4c770-123">Bunu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c770-123">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="4c770-124">Bu, ve ayarı ile yapılabilir `httpsHelpPageEnabled` `httpsHelpPageUrl` .</span><span class="sxs-lookup"><span data-stu-id="4c770-124">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>

<span data-ttu-id="4c770-125">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4c770-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4c770-126">İlk üç işlem (ekleme, çıkarma ve çarpma) başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c770-126">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="4c770-127">Son işlem ("Böl"), sıfıra bölme özel durumuyla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4c770-127">The last operation ("divide") fails with a division by zero exception.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4c770-128">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4c770-128">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4c770-129">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4c770-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4c770-130">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4c770-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="4c770-131">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4c770-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c770-132">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c770-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4c770-133">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4c770-133">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4c770-134">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4c770-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4c770-135">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4c770-135">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
