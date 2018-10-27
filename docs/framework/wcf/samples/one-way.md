---
title: Tek Yönlü
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 9a8af4bcdc76afd96ada595a7234cbc5e0250dfc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180867"
---
# <a name="one-way"></a><span data-ttu-id="ee1ad-102">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="ee1ad-102">One-Way</span></span>
<span data-ttu-id="ee1ad-103">Bu örnek, bir hizmet sözleşmesi ile tek yönlü hizmet işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="ee1ad-104">İstemci, hizmet işlemlerini çift yönlü hizmet işlemleri ile olduğu gibi tamamlanması için beklemez.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="ee1ad-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve kullandığı `wsHttpBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="ee1ad-106">Bu örnekte, alan ve istekleri işleyen hizmet gözlemleyin sağlamak için şirket içinde barındırılan bir konsol uygulaması hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="ee1ad-107">İstemci ayrıca bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-107">The client is also a console application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee1ad-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ee1ad-109">Tek yönlü hizmet sözleşmesi oluşturmak için hizmet sözleşmesini tanımlama, Uygula <xref:System.ServiceModel.OperationContractAttribute> sınıfı her işleme ve ayarlama <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> için `true` aşağıdaki örnek kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="ee1ad-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="ee1ad-110">İstemci hizmet işlemleri tamamlamak beklemez göstermek için aşağıdaki örnek kodda gösterildiği gibi bu örnek hizmeti kodunda bir 5 saniyelik gecikme uygular:</span><span class="sxs-lookup"><span data-stu-id="ee1ad-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="ee1ad-111">İstemci hizmeti çağırıp, çağrı, hizmeti işlemin tamamlanmasını beklemenize gerek kalmadan döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="ee1ad-112">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ee1ad-113">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ee1ad-114">Her konsol penceresi hizmet ve istemci aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="ee1ad-115">İstemci hizmeti önceden tek yönlü hizmet işlemleri için bir istemci beklemez gösteren tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="ee1ad-116">İstemci çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ee1ad-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ee1ad-117">Aşağıdaki hizmet çıktı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ee1ad-117">The following service output is shown:</span></span>  
  
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
>  <span data-ttu-id="ee1ad-118">HTTP, tanımı gereği, bir istek/yanıt protokoldür; bir istekte bulunulduğunda bir yanıt döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="ee1ad-119">Bu, hatta HTTP üzerinden sunulan bir tek yönlü hizmet işlemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="ee1ad-120">İşlem çağrıldığında, hizmet işlemi yürütüldü önce hizmet 202 bir HTTP durum kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="ee1ad-121">Bu durum kodu istek işleme için kabul edildi, ancak işleme henüz tamamlanmamış anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="ee1ad-122">Hizmetten 202 yanıtının alıncaya kadar blokları işlemi çağıran istemci.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="ee1ad-123">Oturumları kullanacak şekilde yapılandırılmış bir bağlama kullanarak birden çok yönlü ileti gönderildiğinde bu bazı beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="ee1ad-124">`wsHttpBinding` Bu örnekte kullanılan bağlama oturumları kullanmak için bir güvenlik bağlamı'kurmak için varsayılan olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="ee1ad-125">Varsayılan olarak, bir oturumda ileti bunlar gönderildiği sırada ulşamasını garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="ee1ad-126">Bir oturumda ikinci bir ileti gönderildiğinde, ilk iletiyi işleyene kadar bu nedenle, bu işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="ee1ad-127">Bunun sonucu olarak, önceki iletinin işlenmesi tamamlanıncaya kadar istemci 202 yanıtının bir ileti almadığında ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="ee1ad-128">İstemci için bu nedenle görünür her bir sonraki işlemi çağrısının blok.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="ee1ad-129">Bu davranışı önlemek için bu örnek, çalışma zamanının eşzamanlı olarak işlemek için ayrı örnekleri iletiler gönderme yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="ee1ad-130">Örnek kümelerini <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> için `PerCall` böylece her ileti farklı bir örneği tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="ee1ad-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ayarlanır `Multiple` teker teker iletilerini dağıtmak birden fazla iş parçacığı izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee1ad-132">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ee1ad-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ee1ad-133">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee1ad-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ee1ad-134">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee1ad-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ee1ad-135">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee1ad-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee1ad-136">İstemcisini çalıştıran ve istemci hizmeti kapatılıyor önce bilgisayarı önce hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="ee1ad-137">Hizmet gitmiş olduğundan güvenlik oturumu düzgün bir şekilde istemci kapattığınızda olamaz, bu istemci özel durumu önler.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee1ad-138">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee1ad-139">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee1ad-140">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee1ad-141">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a><span data-ttu-id="ee1ad-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee1ad-142">See Also</span></span>
