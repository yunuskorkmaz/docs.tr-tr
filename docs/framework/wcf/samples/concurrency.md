---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 393c8a79cb60a33203b41a0778176a4d78a9b6ee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585317"
---
# <a name="concurrency"></a><span data-ttu-id="8547a-102">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="8547a-102">Concurrency</span></span>
<span data-ttu-id="8547a-103">Eşzamanlılık örneği, <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.ConcurrencyMode> bir hizmet örneğinin iletileri sıralı olarak veya aynı anda işleme gerekmediğini denetleyen, numaralandırma ile kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8547a-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="8547a-104">Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="8547a-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="8547a-105">Bu örnek, ' den devralan yeni bir sözleşme tanımlar ve `ICalculatorConcurrency` `ICalculator` hizmet eşzamanlılık durumunu incelemek için iki ek işlem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8547a-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="8547a-106">Eşzamanlılık ayarını değiştirerek, istemcisini çalıştırarak davranış değişikliğini gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8547a-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="8547a-107">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="8547a-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8547a-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8547a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8547a-109">Kullanılabilir üç eşzamanlılık modu vardır:</span><span class="sxs-lookup"><span data-stu-id="8547a-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="8547a-110">`Single`: Her hizmet örneği tek seferde bir ileti işler.</span><span class="sxs-lookup"><span data-stu-id="8547a-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="8547a-111">Bu, varsayılan eşzamanlılık modudur.</span><span class="sxs-lookup"><span data-stu-id="8547a-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="8547a-112">`Multiple`: Her hizmet örneği aynı anda birden çok iletiyi işler.</span><span class="sxs-lookup"><span data-stu-id="8547a-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="8547a-113">Bu eşzamanlılık modunu kullanabilmek için hizmet uygulamasının iş parçacığı açısından güvenli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8547a-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="8547a-114">`Reentrant`: Her hizmet örneği tek seferde bir ileti işler, ancak yeniden geçen çağrıları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8547a-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="8547a-115">Hizmet, bu çağrıyı yalnızca aradığında kabul eder. Yer, [ConcurrencyMode.](concurrencymode-reentrant.md) bir örnek örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8547a-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="8547a-116">Eşzamanlılık kullanımı, örnek oluşturma moduyla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8547a-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="8547a-117"><xref:System.ServiceModel.InstanceContextMode.PerCall>Örnek olarak, her ileti yeni bir hizmet örneği tarafından işlendiği için eşzamanlılık ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="8547a-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="8547a-118">Örnek olarak <xref:System.ServiceModel.InstanceContextMode.Single> , <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode.Multiple> tek örneğin iletileri sıralı veya eşzamanlı olarak işleme sunuluna bağlı olarak, ya da eşzamanlılık geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8547a-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="8547a-119"><xref:System.ServiceModel.InstanceContextMode.PerSession>Örnek olarak, herhangi bir eşzamanlılık modu ilgili olabilir.</span><span class="sxs-lookup"><span data-stu-id="8547a-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="8547a-120">Service sınıfı, `[ServiceBehavior(ConcurrencyMode=<setting>)]` Aşağıdaki kod örneğinde gösterildiği gibi özniteliğiyle eşzamanlılık davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8547a-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="8547a-121">Hangi satırların açıklama olarak değiştirilerek, `Single` ve `Multiple` eşzamanlılık modlarıyla denemeler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8547a-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="8547a-122">Eşzamanlılık modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8547a-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="8547a-123">Örnek, <xref:System.ServiceModel.ConcurrencyMode.Multiple> Varsayılan olarak örnek oluşturma ile eşzamanlılık kullanır <xref:System.ServiceModel.InstanceContextMode.Single> .</span><span class="sxs-lookup"><span data-stu-id="8547a-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="8547a-124">İstemci kodu, zaman uyumsuz bir ara sunucu kullanacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8547a-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="8547a-125">Bu, istemcinin her bir çağrı arasında yanıt beklemeden hizmete birden çok çağrı yapmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8547a-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="8547a-126">Hizmet eşzamanlılık modunun davranışındaki farkı gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8547a-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="8547a-127">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8547a-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8547a-128">Hizmetin altında çalıştığı eşzamanlılık modu görüntülenir, her bir işlem çağrılır ve sonra işlem sayısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8547a-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="8547a-129">Eşzamanlılık modu olduğunda `Multiple` , hizmet birden çok iletiyi eşzamanlı olarak işlediği için sonuçların nasıl çağrıldıklarından farklı bir sırada döndürüldiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8547a-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="8547a-130">Eşzamanlılık modunu olarak değiştirerek `Single` , hizmet her iletiyi sırayla işleyerek sonuçlar çağrıldıkları sırada döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8547a-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="8547a-131">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8547a-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8547a-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8547a-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8547a-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8547a-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8547a-134">Proxy istemcisini oluşturmak için Svcutil. exe ' yi kullanırsanız, seçeneğini de bulundurtığınızdan emin olun `/async` .</span><span class="sxs-lookup"><span data-stu-id="8547a-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="8547a-135">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8547a-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="8547a-136">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8547a-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8547a-137">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8547a-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8547a-138">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8547a-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8547a-139">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8547a-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8547a-140">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8547a-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
