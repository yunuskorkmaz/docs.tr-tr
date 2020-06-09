---
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 53f21129860c644d09d1a2eb9cb956aecf8ab0ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596649"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="716df-102">Hizmet Hata Ayıklama Davranışı</span><span class="sxs-lookup"><span data-stu-id="716df-102">Service Debug Behavior</span></span>

<span data-ttu-id="716df-103">Bu örnek, hizmet hata ayıklama davranışı ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="716df-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="716df-104">Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="716df-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="716df-105">Bu örnek, yapılandırma dosyasında hizmet hata ayıklama davranışını açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="716df-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="716df-106">Ayrıca, kod içinde imperatively de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="716df-106">It can also be done imperatively in code.</span></span>

<span data-ttu-id="716df-107">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="716df-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="716df-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="716df-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="716df-109">Sunucu için Web. config dosyası, aşağıdaki örnekte gösterildiği gibi yardım sayfası ve özel durum işlemeyi etkinleştirmek için hizmet hata ayıklama davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="716df-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>

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

<span data-ttu-id="716df-110">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md), hizmet hata ayıklama davranışı özelliklerinin değiştirilmesini sağlayan yapılandırma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="716df-110">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="716df-111">Kullanıcı bu davranışı değiştirerek aşağıdakileri elde edebilir:</span><span class="sxs-lookup"><span data-stu-id="716df-111">The user can modify this behavior to achieve the following:</span></span>

- <span data-ttu-id="716df-112">Bu, özel durum kullanılarak bildirilmemiş olsa bile hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar <xref:System.ServiceModel.FaultContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="716df-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="716df-113">Ayarıyla yapılır `includeExceptionDetailInFaults` `true` .</span><span class="sxs-lookup"><span data-stu-id="716df-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="716df-114">Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="716df-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="716df-115">Bu ayarı bir üretim ortamında açmak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="716df-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="716df-116">Beklenmeyen bir sunucu özel durumu, istemciye yönelik amaçlı olmayan bazı bilgiler içerebilir ve bu nedenle ayarı `includeExceptionDetailsInFaults` `true` bilgi sızıntısına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="716df-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>

- <span data-ttu-id="716df-117">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)Ayrıca, bir kullanıcının yardım sayfasını etkinleştirmesine veya devre dışı bırakmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="716df-117">The [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="716df-118">Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir.</span><span class="sxs-lookup"><span data-stu-id="716df-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="716df-119">Bu, ayarına göre etkinleştirilebilir `httpHelpPageEnabled` `true` .</span><span class="sxs-lookup"><span data-stu-id="716df-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="716df-120">Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="716df-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="716df-121">Başka bir öznitelik ayarlayarak bu adresi değiştirebilirsiniz `httpHelpPageUrl` .</span><span class="sxs-lookup"><span data-stu-id="716df-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="716df-122">Bunu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="716df-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="716df-123">Bu, ve ayarı ile yapılabilir `httpsHelpPageEnabled` `httpsHelpPageUrl` .</span><span class="sxs-lookup"><span data-stu-id="716df-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>

<span data-ttu-id="716df-124">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="716df-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="716df-125">İlk üç işlem (ekleme, çıkarma ve çarpma) başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="716df-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="716df-126">Son işlem ("Böl"), sıfıra bölme özel durumuyla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="716df-126">The last operation ("divide") fails with a division by zero exception.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="716df-127">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="716df-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="716df-128">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="716df-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="716df-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="716df-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="716df-130">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="716df-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="716df-131">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="716df-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="716df-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="716df-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="716df-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="716df-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="716df-134">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="716df-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
