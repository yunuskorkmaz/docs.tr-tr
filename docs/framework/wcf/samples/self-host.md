---
title: Kendini Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a1758ef83adf11cdeee8bd3560ad2275985b3788
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155398"
---
# <a name="self-host"></a><span data-ttu-id="4b443-102">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="4b443-102">Self-Host</span></span>
<span data-ttu-id="4b443-103">Bu örnek, şirket içinde barındırılan hizmeti bir konsol uygulamasında uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b443-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="4b443-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4b443-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="4b443-105">Hizmet yapılandırma dosyası için App.config Web.config dosyasından olarak yeniden adlandırıldı ve ana bilgisayar kullanan bir taban adresini yapılandırmak için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4b443-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="4b443-106">Statik uygulamak için hizmet kaynak kodu değiştirilmiş `Main` oluşturur ve yapılandırılmış temel adresini sağlayan bir hizmet konağı açar işlevi.</span><span class="sxs-lookup"><span data-stu-id="4b443-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="4b443-107">Hizmet uygulaması, her işlem için konsola çıkışını yazmak için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="4b443-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="4b443-108">İstemci, hizmetin doğru uç nokta adresini yapılandırma dışında değiştirilmemiş olmuştur.</span><span class="sxs-lookup"><span data-stu-id="4b443-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b443-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4b443-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4b443-110">Örneği oluşturmak için bir statik main işlevi uygulayan bir <xref:System.ServiceModel.ServiceHost> için verilen `CalculatorService` , aşağıdaki örnek kodda gösterildiği gibi yazın.</span><span class="sxs-lookup"><span data-stu-id="4b443-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="4b443-111">Bir hizmeti Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırılan hizmetin taban adresi barındırma ortamı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4b443-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="4b443-112">Şirket içinde barındırılan durumda kendiniz temel adresini belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4b443-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="4b443-113">Bu yapılır kullanarak `add` öğe, alt [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), alt [ \<konak >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), alt [ \<hizmet > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4b443-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="4b443-114">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4b443-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4b443-115">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4b443-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b443-116">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4b443-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4b443-117">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b443-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4b443-118">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b443-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4b443-119">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b443-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4b443-120">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="4b443-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4b443-121">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4b443-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4b443-122">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4b443-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b443-123">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4b443-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="4b443-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b443-124">See Also</span></span>  
 [<span data-ttu-id="4b443-125">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="4b443-125">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
