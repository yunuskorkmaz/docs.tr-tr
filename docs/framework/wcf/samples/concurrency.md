---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 5de918f71f4361af3409c8382781844824747c83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296608"
---
# <a name="concurrency"></a><span data-ttu-id="be162-102">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="be162-102">Concurrency</span></span>
<span data-ttu-id="be162-103">Eşzamanlılık örneği kullanmayı gösterir <xref:System.ServiceModel.ServiceBehaviorAttribute> ile <xref:System.ServiceModel.ConcurrencyMode> sabit listesi bir hizmet örneği sırayla veya aynı anda iletileri işleyen olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="be162-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="be162-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="be162-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="be162-105">Bu örnek yeni bir sözleşme tanımlayan `ICalculatorConcurrency`, işlevinden devralan `ICalculator`, hizmet eşzamanlılık durumunu incelemek için iki ek işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be162-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="be162-106">Eş zamanlılık ayarı değiştirerek istemci çalıştırarak davranış değişikliği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be162-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="be162-107">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="be162-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be162-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="be162-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="be162-109">Üç eşzamanlılık modu vardır:</span><span class="sxs-lookup"><span data-stu-id="be162-109">There are three concurrency modes available:</span></span>  
  
-   <span data-ttu-id="be162-110">`Single`: Her hizmet örneği aynı anda tek bir ileti işler.</span><span class="sxs-lookup"><span data-stu-id="be162-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="be162-111">Varsayılan eşzamanlılık modu budur.</span><span class="sxs-lookup"><span data-stu-id="be162-111">This is the default concurrency mode.</span></span>  
  
-   <span data-ttu-id="be162-112">`Multiple`: Her hizmet örneği birden çok iletiyi eş zamanlı olarak işler.</span><span class="sxs-lookup"><span data-stu-id="be162-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="be162-113">Hizmet uygulaması bu eşzamanlılık modu kullanmak için iş parçacığı açısından güvenli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="be162-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   <span data-ttu-id="be162-114">`Reentrant`: Her hizmet örneği, tek bir ileti işler, ancak desteklemeyeceğini çağrılarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="be162-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="be162-115">Bunu çağırma yaparken hizmeti yalnızca bu çağrıları kabul eder. ConcurrencyMode için Reentrant gösterilmiştir [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="be162-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="be162-116">Eşzamanlılık kullanımını örneklemesini moduna ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="be162-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="be162-117">İçinde <xref:System.ServiceModel.InstanceContextMode.PerCall> yeni bir hizmet örneği tarafından işlenen her iletisi depolamasına, eşzamanlılık ilgili değildir, çünkü.</span><span class="sxs-lookup"><span data-stu-id="be162-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="be162-118">İçinde <xref:System.ServiceModel.InstanceContextMode.Single> depolamasına, ya da <xref:System.ServiceModel.ConcurrencyMode.Single> veya <xref:System.ServiceModel.ConcurrencyMode.Multiple> olup olmadığı tek örnekli iletileri sırayla veya aynı anda işler bağlı olarak, ilgili eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="be162-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="be162-119">İçinde <xref:System.ServiceModel.InstanceContextMode.PerSession> depolamasına, eşzamanlılık modun herhangi birinde uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="be162-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="be162-120">Hizmet sınıfı ile eşzamanlılık davranışı belirtir `[ServiceBehavior(ConcurrencyMode=<setting>)]` özniteliği aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="be162-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="be162-121">Hangi satırlar açıklama satırlarıdır değiştirerek deneme yapabileceğiniz `Single` ve `Multiple` eşzamanlılık modu.</span><span class="sxs-lookup"><span data-stu-id="be162-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="be162-122">Eşzamanlılık modu değiştirdikten sonra hizmeti yeniden unutmayın.</span><span class="sxs-lookup"><span data-stu-id="be162-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="be162-123">Örnek kullanır <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık ile <xref:System.ServiceModel.InstanceContextMode.Single> varsayılan örnek oluşturma.</span><span class="sxs-lookup"><span data-stu-id="be162-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="be162-124">İstemci kodu, zaman uyumsuz bir ara sunucusunu kullanacak şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="be162-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="be162-125">Bu, istemci arasındaki her çağrı bir yanıt beklemeden birden çok hizmete çağrı yapma sağlar.</span><span class="sxs-lookup"><span data-stu-id="be162-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="be162-126">Hizmet eşzamanlılık modu davranıştaki farkı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be162-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="be162-127">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="be162-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="be162-128">Hizmetinin altında çalışmakta olduğu eşzamanlılık modu görüntülenir, her işlem çağrılır ve sonra işlem sayısını görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="be162-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="be162-129">Eşzamanlılık modu olduğunda dikkat `Multiple`nasıl çağrılan daha farklı bir sırada döndürülen sonuçları, hizmet işlediğinden birden çok eşzamanlı olarak iletileri.</span><span class="sxs-lookup"><span data-stu-id="be162-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="be162-130">İçin eşzamanlılık modu değiştirerek `Single`, hizmetin her ileti sıralı olarak işlediğinden, sonuçları çağrılır, sırayla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="be162-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="be162-131">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="be162-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="be162-132">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="be162-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="be162-133">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be162-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="be162-134">Proxy istemcisi üretmek için Svcutil.exe kullanma eklediğinizden emin olun `/async` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="be162-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="be162-135">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be162-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="be162-136">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be162-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="be162-137">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="be162-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="be162-138">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="be162-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="be162-139">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="be162-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be162-140">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="be162-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
