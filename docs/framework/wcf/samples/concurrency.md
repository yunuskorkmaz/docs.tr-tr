---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183940"
---
# <a name="concurrency"></a><span data-ttu-id="81283-102">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="81283-102">Concurrency</span></span>
<span data-ttu-id="81283-103">Eşzamanlılık örneği, bir <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmetin <xref:System.ServiceModel.ConcurrencyMode> bir örneğinin iletileri sırayla mı yoksa aynı anda mı işlediğini kontrol eden numaralandırma ile birlikte kullanılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="81283-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="81283-104">Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır.</span><span class="sxs-lookup"><span data-stu-id="81283-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="81283-105">Bu örnek, `ICalculatorConcurrency`hizmet eşzamanlılık durumunu denetlemek `ICalculator`için iki ek işlem sağlayan, devralan yeni bir sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81283-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="81283-106">Eşzamanlılık ayarını değiştirerek, istemciyi çalıştırarak davranış değişikliğini gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81283-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="81283-107">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="81283-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81283-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="81283-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="81283-109">Üç eşzamanlılık modu vardır:</span><span class="sxs-lookup"><span data-stu-id="81283-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="81283-110">`Single`: Her hizmet örneği aynı anda bir iletiyi işler.</span><span class="sxs-lookup"><span data-stu-id="81283-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="81283-111">Bu varsayılan eşzamanlılık modudur.</span><span class="sxs-lookup"><span data-stu-id="81283-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="81283-112">`Multiple`: Her hizmet örneği aynı anda birden çok iletiyi işler.</span><span class="sxs-lookup"><span data-stu-id="81283-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="81283-113">Bu eşzamanlılık modunu kullanmak için hizmet uygulaması iş parçacığı güvenli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="81283-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="81283-114">`Reentrant`: Her hizmet örneği aynı anda bir iletiyi işler, ancak reentrant çağrılarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="81283-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="81283-115">Hizmet bu çağrıları yalnızca çağrı yaparken kabul eder. Reentrant [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) örnek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="81283-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="81283-116">Eşzamanlılık kullanımı instancing modu ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="81283-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="81283-117">Her <xref:System.ServiceModel.InstanceContextMode.PerCall> ileti yeni bir hizmet örneği tarafından işlendiğinden, eşzamanlılık instancing olarak ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="81283-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="81283-118">Tek <xref:System.ServiceModel.InstanceContextMode.Single> bir örneğin iletileri <xref:System.ServiceModel.ConcurrencyMode.Multiple> sırayla mı yoksa eş zamanlı olarak mı işlediğine bağlı olarak, instancing olarak, ya da <xref:System.ServiceModel.ConcurrencyMode.Single> eşzamanlılık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="81283-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="81283-119">Instancing <xref:System.ServiceModel.InstanceContextMode.PerSession> olarak, eşzamanlılık modları herhangi ilgili olabilir.</span><span class="sxs-lookup"><span data-stu-id="81283-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="81283-120">Hizmet sınıfı, öznitelik ile `[ServiceBehavior(ConcurrencyMode=<setting>)]` eşzamanlılık davranışını aşağıdaki kod örneğinde gösterildiği gibi belirtir.</span><span class="sxs-lookup"><span data-stu-id="81283-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="81283-121">Hangi satırların yorumlanabileceğini değiştirerek, `Single` eşzamanlılık modlarını deneyebilirsiniz. `Multiple`</span><span class="sxs-lookup"><span data-stu-id="81283-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="81283-122">Eşzamanlılık modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="81283-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="81283-123">Örnek temerrüt <xref:System.ServiceModel.InstanceContextMode.Single> tarafından instancing ile eşzamanlılık kullanır. <xref:System.ServiceModel.ConcurrencyMode.Multiple></span><span class="sxs-lookup"><span data-stu-id="81283-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="81283-124">İstemci kodu eşzamanlı proxy kullanmak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="81283-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="81283-125">Bu, istemcinin her arama arasında yanıt beklemeden hizmete birden çok arama yapmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="81283-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="81283-126">Hizmet eşzamanlılık modunun davranışındaki farkı gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81283-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="81283-127">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="81283-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="81283-128">Hizmetin altında çalıştırdığı eşzamanlılık modu görüntülenir, her işlem çağrılır ve işlem sayısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="81283-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="81283-129">Eşzamanlılık modu `Multiple`olduğunda, hizmet aynı anda birden çok iletiyi işlediği için, sonuçların çağrıldıkları şekilden farklı bir sırada döndürüldüye dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="81283-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="81283-130">Eşzamanlılık modunu `Single`değiştirerek, her iletiyi sırayla işler, çünkü hizmet çağrıldıkları sırada döndürülür.</span><span class="sxs-lookup"><span data-stu-id="81283-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="81283-131">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="81283-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="81283-132">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="81283-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="81283-133">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="81283-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="81283-134">Proxy istemcisini oluşturmak için Svcutil.exe kullanıyorsanız, `/async` seçeneği eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="81283-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="81283-135">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="81283-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="81283-136">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="81283-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="81283-137">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="81283-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81283-138">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="81283-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="81283-139">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="81283-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81283-140">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="81283-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
