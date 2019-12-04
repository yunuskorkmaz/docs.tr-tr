---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 1342e50a5dca56260f832f5e0d684f4f79d355e2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715996"
---
# <a name="concurrency"></a><span data-ttu-id="1591c-102">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="1591c-102">Concurrency</span></span>
<span data-ttu-id="1591c-103">Eşzamanlılık örneği, bir hizmet örneğinin iletileri sıralı veya eşzamanlı olarak işleme gerekmediğini denetleyen <xref:System.ServiceModel.ConcurrencyMode> numaralandırmada <xref:System.ServiceModel.ServiceBehaviorAttribute> kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1591c-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="1591c-104">Örnek, `ICalculator` hizmet sözleşmesini uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="1591c-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="1591c-105">Bu örnek, `ICalculator`devralan `ICalculatorConcurrency`yeni bir sözleşme tanımlar ve hizmetin eşzamanlılık durumunu incelemek için iki ek işlem sağlar.</span><span class="sxs-lookup"><span data-stu-id="1591c-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="1591c-106">Eşzamanlılık ayarını değiştirerek, istemcisini çalıştırarak davranış değişikliğini gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1591c-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="1591c-107">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="1591c-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1591c-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1591c-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1591c-109">Kullanılabilir üç eşzamanlılık modu vardır:</span><span class="sxs-lookup"><span data-stu-id="1591c-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="1591c-110">`Single`: her hizmet örneği tek seferde bir ileti işler.</span><span class="sxs-lookup"><span data-stu-id="1591c-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="1591c-111">Bu, varsayılan eşzamanlılık modudur.</span><span class="sxs-lookup"><span data-stu-id="1591c-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="1591c-112">`Multiple`: her hizmet örneği aynı anda birden çok iletiyi işler.</span><span class="sxs-lookup"><span data-stu-id="1591c-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="1591c-113">Bu eşzamanlılık modunu kullanabilmek için hizmet uygulamasının iş parçacığı açısından güvenli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1591c-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="1591c-114">`Reentrant`: her hizmet örneği tek seferde bir ileti işler, ancak yeniden geçen çağrıları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1591c-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="1591c-115">Hizmet, bu çağrıyı yalnızca aradığında kabul eder. Yer, [ConcurrencyMode.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) bir örnek örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1591c-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="1591c-116">Eşzamanlılık kullanımı, örnek oluşturma moduyla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="1591c-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="1591c-117"><xref:System.ServiceModel.InstanceContextMode.PerCall> örnek oluşturma, her ileti yeni bir hizmet örneği tarafından işlendiği için eşzamanlılık ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="1591c-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="1591c-118"><xref:System.ServiceModel.InstanceContextMode.Single> örnek oluşturma bölümünde, tek örneğin iletileri sıralı veya eşzamanlı olarak işleme sunuluna bağlı olarak, <xref:System.ServiceModel.ConcurrencyMode.Single> veya <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1591c-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="1591c-119"><xref:System.ServiceModel.InstanceContextMode.PerSession> örnek oluşturma bölümünde eşzamanlılık modlarından herhangi biri ilgili olabilir.</span><span class="sxs-lookup"><span data-stu-id="1591c-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="1591c-120">Service sınıfı, aşağıdaki kod örneğinde gösterildiği gibi `[ServiceBehavior(ConcurrencyMode=<setting>)]` özniteliğiyle eşzamanlılık davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1591c-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="1591c-121">Hangi satırların açıklama olarak değiştirilerek `Single` ve `Multiple` eşzamanlılık modlarını deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1591c-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="1591c-122">Eşzamanlılık modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1591c-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="1591c-123">Örnek, varsayılan olarak <xref:System.ServiceModel.InstanceContextMode.Single> örnekleyerek <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık kullanır.</span><span class="sxs-lookup"><span data-stu-id="1591c-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="1591c-124">İstemci kodu, zaman uyumsuz bir ara sunucu kullanacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1591c-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="1591c-125">Bu, istemcinin her bir çağrı arasında yanıt beklemeden hizmete birden çok çağrı yapmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1591c-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="1591c-126">Hizmet eşzamanlılık modunun davranışındaki farkı gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1591c-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="1591c-127">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1591c-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1591c-128">Hizmetin altında çalıştığı eşzamanlılık modu görüntülenir, her bir işlem çağrılır ve sonra işlem sayısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1591c-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="1591c-129">Eşzamanlılık modu `Multiple`olduğunda, hizmet birden çok iletiyi eşzamanlı olarak işlediği için sonuçların nasıl çağrıldıklarından farklı bir sırada döndürüldiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1591c-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="1591c-130">Eşzamanlılık modunu `Single`olarak değiştirerek, hizmet her iletiyi sırayla işleyerek sonuçlar çağrıldıkları sırada döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1591c-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="1591c-131">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1591c-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1591c-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1591c-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1591c-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1591c-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1591c-134">Proxy istemcisini oluşturmak için Svcutil. exe ' yi kullanırsanız, `/async` seçeneğini de bulundurtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1591c-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="1591c-135">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1591c-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="1591c-136">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1591c-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1591c-137">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1591c-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1591c-138">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1591c-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1591c-139">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="1591c-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1591c-140">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1591c-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
