---
title: Tek Yönlü
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 0035b64b14b0d32f39974e8eaa28242290d665c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957239"
---
# <a name="one-way"></a><span data-ttu-id="1464b-102">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="1464b-102">One-Way</span></span>
<span data-ttu-id="1464b-103">Bu örnekte, tek yönlü hizmet işlemlerine sahip bir hizmet kişisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1464b-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="1464b-104">İstemci, iki yönlü hizmet işlemlerinde olduğu gibi hizmet işlemlerinin tamamlanmasını beklemez.</span><span class="sxs-lookup"><span data-stu-id="1464b-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="1464b-105">Bu örnek, [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) başlama ve `wsHttpBinding` bağlamayı kullanma tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="1464b-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="1464b-106">Bu örnekteki hizmet, istekleri alan ve işleyen hizmeti gözlemlemenizi sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1464b-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="1464b-107">İstemci Ayrıca bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1464b-107">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1464b-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1464b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1464b-109">Tek yönlü bir hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın, her bir işleme <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulayın ve aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` gibi olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="1464b-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="1464b-110">İstemcinin hizmet işlemlerinin tamamlanmasını beklemediğini göstermek için, bu örnekteki hizmet kodu aşağıdaki örnek kodda gösterildiği gibi beş saniyelik bir gecikme uygular:</span><span class="sxs-lookup"><span data-stu-id="1464b-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="1464b-111">İstemci hizmeti çağırdığında, çağrı, hizmet işleminin tamamlanmasını beklememeden geri döner.</span><span class="sxs-lookup"><span data-stu-id="1464b-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="1464b-112">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1464b-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1464b-113">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1464b-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="1464b-114">Her bir konsol penceresinde, hem hizmeti hem de istemcisini kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1464b-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="1464b-115">İstemci, bir istemcinin tek yönlü hizmet işlemlerinin tamamlanmasını beklemez olduğunu gösteren hizmetin önünde tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="1464b-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="1464b-116">İstemci çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1464b-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1464b-117">Aşağıdaki hizmet çıktısı gösterilir:</span><span class="sxs-lookup"><span data-stu-id="1464b-117">The following service output is shown:</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> <span data-ttu-id="1464b-118">HTTP, tanım, istek/yanıt protokolü; istek yapıldığında bir yanıt döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1464b-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="1464b-119">Bu, HTTP üzerinden kullanıma sunulan tek yönlü bir hizmet işlemi için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1464b-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="1464b-120">İşlem çağrıldığında hizmet, hizmet işlemi yürütülmeden önce 202 HTTP durum kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1464b-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="1464b-121">Bu durum kodu, isteğin işleme için kabul edildiği anlamına gelir, ancak işlem henüz tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="1464b-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="1464b-122">İşlemi çağıran istemci, hizmetten 202 yanıtını alıncaya kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="1464b-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="1464b-123">Bu, oturumları kullanmak üzere yapılandırılmış bir bağlama kullanılarak birden çok tek yönlü ileti gönderildiğinde beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1464b-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="1464b-124">Bu `wsHttpBinding` örnekte kullanılan bağlama, varsayılan olarak bir güvenlik bağlamı oluşturmak için oturumları kullanacak şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1464b-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="1464b-125">Varsayılan olarak, bir oturumdaki iletilerin gönderildikleri sırada gelmesi garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="1464b-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="1464b-126">Bu nedenle, bir oturumdaki ikinci ileti gönderildiğinde, ilk ileti işlenene kadar işlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="1464b-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="1464b-127">Bunun sonucunda, istemcinin önceki iletinin işlenmesi tamamlanana kadar bir ileti için 202 yanıtını almamıştır.</span><span class="sxs-lookup"><span data-stu-id="1464b-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="1464b-128">Bu nedenle, istemci sonraki işlem çağrısındaki blok olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="1464b-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="1464b-129">Bu davranışı önlemek için, bu örnek çalışma zamanını, işleme için farklı örneklere eşzamanlı olarak ileti göndermek üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1464b-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="1464b-130">Örnek, her <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> iletinin `PerCall` farklı bir örnek tarafından işlenebilmesi için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1464b-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="1464b-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>, tek seferde `Multiple` ileti gönderimi için birden fazla iş parçacığına izin vermek üzere olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1464b-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1464b-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1464b-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1464b-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1464b-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1464b-134">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1464b-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1464b-135">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1464b-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1464b-136">İstemcisini çalıştırmadan önce hizmeti çalıştırın ve hizmeti kapatmadan önce istemciyi kapatın.</span><span class="sxs-lookup"><span data-stu-id="1464b-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="1464b-137">Bu, hizmet kaybolduğu için istemci güvenlik oturumunu düzgün bir şekilde kapatamadığında istemci özel durumunu önler.</span><span class="sxs-lookup"><span data-stu-id="1464b-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1464b-138">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1464b-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1464b-139">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1464b-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1464b-140">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="1464b-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1464b-141">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1464b-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
