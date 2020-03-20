---
title: Kendini Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a38738c369db3d3f8242bd71ee04a19a669b2cf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144155"
---
# <a name="self-host"></a><span data-ttu-id="84461-102">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="84461-102">Self-Host</span></span>
<span data-ttu-id="84461-103">Bu örnek, konsol uygulamasında kendi kendine barındırılan bir hizmetin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="84461-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="84461-104">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84461-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="84461-105">Hizmet yapılandırma dosyası Web.config'den App.config'e yeniden adlandırıldı ve ana bilgisayar tarafından kullandığı bir temel adresi yapılandırmak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="84461-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="84461-106">Hizmet kaynak kodu, yapılandırılan temel `Main` adresi sağlayan bir hizmet ana bilgisayarı oluşturan ve açan statik bir işlev uygulamak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="84461-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="84461-107">Hizmet uygulaması, her işlem için konsola çıktı yazmak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="84461-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="84461-108">Hizmetin doğru bitiş noktası adresini yapılandırmak dışında istemci değiştirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="84461-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84461-109">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="84461-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="84461-110">Örnek, aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.ServiceHost> gibi, `CalculatorService` verilen tür için bir oluşturmak için statik bir main işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="84461-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="84461-111">Bir hizmet Internet Information Services (IIS) veya Windows Process Etkinleştirme Hizmeti'nde (WAS) barındırıldığında, hizmetin temel adresi barındırma ortamı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="84461-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="84461-112">Kendi kendine barındırılan durumda, temel adresi kendiniz belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="84461-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="84461-113">Bu, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) [ \<aşağıdaki ](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)örnek yapılandırmada gösterildiği gibi, temelAdresler>, ev sahibi>, hizmet in alt>alt adresler alt kullanılarak yapılır. `add`</span><span class="sxs-lookup"><span data-stu-id="84461-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="84461-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="84461-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="84461-115">Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="84461-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="84461-116">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="84461-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="84461-117">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="84461-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="84461-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="84461-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="84461-119">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="84461-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="84461-120">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="84461-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="84461-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="84461-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="84461-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="84461-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84461-123">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="84461-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="84461-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84461-124">See also</span></span>

- <span data-ttu-id="84461-125">[AppFabric Hosting ve Kalıcılık Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="84461-125">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
