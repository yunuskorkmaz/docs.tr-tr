---
title: Kendini Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 544ae8c0bc88d49c281810714225dbadecfd443b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558426"
---
# <a name="self-host"></a><span data-ttu-id="aea0c-102">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="aea0c-102">Self-Host</span></span>
<span data-ttu-id="aea0c-103">Bu örnek, bir konsol uygulamasında kendi kendine barındırılan bir hizmetin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aea0c-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="aea0c-104">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="aea0c-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="aea0c-105">Hizmet yapılandırma dosyası, Web.config App.config olarak yeniden adlandırıldı ve konağın kullandığı bir temel adresi yapılandırmak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="aea0c-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="aea0c-106">Hizmet kaynak kodu, `Main` yapılandırılmış temel adresi sağlayan bir hizmet ana bilgisayarı oluşturup açan bir statik işlevi uygulayacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aea0c-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="aea0c-107">Hizmet uygulamasının her işlem için konsola çıkış yazacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aea0c-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="aea0c-108">Hizmetin doğru uç nokta adresini yapılandırma dışında, istemci değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="aea0c-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aea0c-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="aea0c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="aea0c-110">Örnek, <xref:System.ServiceModel.ServiceHost> `CalculatorService` Aşağıdaki örnek kodda gösterildiği gibi, verilen tür için oluşturmak üzere bir statik Main işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="aea0c-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="aea0c-111">Bir hizmet Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) içinde barındırılıyorsa, hizmetin temel adresi barındırma ortamı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="aea0c-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="aea0c-112">Şirket içinde barındırılan durumda, temel adresi kendiniz belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aea0c-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="aea0c-113">Bu, `add` [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) [\<host>](../../configure-apps/file-schema/wcf/host.md) [\<service>](../../configure-apps/file-schema/wcf/service.md) Aşağıdaki örnek yapılandırmada gösterildiği gibi, alt öğesinin alt öğesi, öğesinin alt öğesi kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="aea0c-113">This is done using the `add` element, child of [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../configure-apps/file-schema/wcf/host.md), child of [\<service>](../../configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="aea0c-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aea0c-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="aea0c-115">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="aea0c-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aea0c-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="aea0c-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="aea0c-117">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="aea0c-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="aea0c-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="aea0c-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="aea0c-119">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="aea0c-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aea0c-120">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="aea0c-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="aea0c-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="aea0c-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="aea0c-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="aea0c-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aea0c-123">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="aea0c-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="aea0c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aea0c-124">See also</span></span>

- <span data-ttu-id="aea0c-125">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="aea0c-125">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
