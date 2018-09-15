---
title: Örnek Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1d193b0cac56f365a4f0a294145369502754a1b1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658788"
---
# <a name="instancing"></a><span data-ttu-id="9ee21-102">Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ee21-102">Instancing</span></span>
<span data-ttu-id="9ee21-103">İstemci isteklerine yanıt olarak bir hizmet sınıfı örneğini nasıl oluşturulduğunu denetimleri örneklemesini davranış ayarına Instancing örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ee21-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="9ee21-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="9ee21-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="9ee21-105">Bu örnek yeni bir sözleşme tanımlayan `ICalculatorInstance`, işlevinden devralan `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="9ee21-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="9ee21-106">Belirtilen sözleşme `ICalculatorInstance` hizmet örneği durumunu incelemek için üç ek işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ee21-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="9ee21-107">Örneklemesini ayarı değiştirerek istemci çalıştırarak davranış değişikliği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ee21-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="9ee21-108">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="9ee21-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ee21-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="9ee21-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9ee21-110">Aşağıdaki örneklemesini modları kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9ee21-110">The following instancing modes are available:</span></span>  
  
-   <span data-ttu-id="9ee21-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Yeni bir hizmet örneği, her istemci isteği için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9ee21-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
-   <span data-ttu-id="9ee21-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Yeni bir örneği, her yeni istemci oturumu için oluşturulan ve (oturum destekleyen bir bağlama gerektirir), oturumunun ömrü boyunca saklanır.</span><span class="sxs-lookup"><span data-stu-id="9ee21-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
-   <span data-ttu-id="9ee21-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Tek bir hizmet sınıfı örneğini uygulama ömrü boyunca tüm istemci isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="9ee21-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="9ee21-114">Hizmet sınıfı ile örneklemesini davranışını belirten `[ServiceBehavior(InstanceContextMode=<setting>)]` özniteliği aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="9ee21-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="9ee21-115">Satırları değiştirerek açıklamalı, her örneği modun davranışını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ee21-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="9ee21-116">Örneklemesini modu değiştirdikten sonra hizmeti yeniden unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9ee21-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="9ee21-117">İstemcide belirtmek için hiçbir örnek oluşturma ile ilgili ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="9ee21-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```  
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="9ee21-118">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9ee21-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9ee21-119">Hizmetinin altında çalışmakta olduğu örnek modu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9ee21-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="9ee21-120">Her işlemden sonra örnek kimliği ve işlem sayısı örneklemesini modu davranışını yansıtacak şekilde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9ee21-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="9ee21-121">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9ee21-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ee21-122">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9ee21-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9ee21-123">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ee21-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9ee21-124">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ee21-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9ee21-125">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ee21-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ee21-126">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="9ee21-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ee21-127">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9ee21-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ee21-128">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9ee21-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ee21-129">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9ee21-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
  
## <a name="see-also"></a><span data-ttu-id="9ee21-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ee21-130">See Also</span></span>
