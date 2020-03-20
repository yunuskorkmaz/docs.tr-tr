---
title: ConcurrencyMode Yeniden Girme
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183903"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="4da42-102">ConcurrencyMode Yeniden Girme</span><span class="sxs-lookup"><span data-stu-id="4da42-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="4da42-103">Bu örnek, concurrencyMode.Reentrant'ı bir hizmet uygulamasında kullanmanın gerekliliğini ve sonuçlarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4da42-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="4da42-104">ConcurrencyMode.Reentrant, hizmetin (veya geri aramanın) belirli bir zamanda yalnızca `ConcurencyMode.Single`bir iletiyi işlediğini (benzer şekilde) ifade eder.</span><span class="sxs-lookup"><span data-stu-id="4da42-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="4da42-105">İş parçacığı güvenliğini sağlamak için, Windows Communication `InstanceContext` Foundation (WCF) başka iletilerin işlenememesi için bir iletiyi işlemeyi kilitler.</span><span class="sxs-lookup"><span data-stu-id="4da42-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="4da42-106">Reentrant modu durumunda, `InstanceContext` hizmet böylece sonraki arama, (örnek gösterildiği gibi reentrant olabilir) hizmete bir dahaki sefere kilit almak için izin giden bir arama yapmadan hemen önce kilidi açılır.</span><span class="sxs-lookup"><span data-stu-id="4da42-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="4da42-107">Davranışı göstermek için örnek, istemci ve hizmetin çift yönlü bir sözleşme kullanarak birbirleri arasında nasıl ileti gönderebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4da42-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="4da42-108">Tanımlanan sözleşme, hizmet tarafından uygulanan `Ping` yöntem ve istemci tarafından uygulanan geri `Pong` arama yöntemi ile çift yönlü bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="4da42-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="4da42-109">İstemci, sunucunun `Ping` yöntemini kene sayısıyla çağırır ve ardından aramayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="4da42-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="4da42-110">Hizmet, onay sayısının 0'a eşit olup olmadığını denetler `Pong` ve onay sayısını azalırken geri arama yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="4da42-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="4da42-111">Bu, örnekteki aşağıdaki kod tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="4da42-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 Geri aramanın `Pong` `Ping` uygulaması, uygulamayla aynı mantığa sahiptir. Diğer bir deyişle, onay sayısının sıfır olup olmadığını `Ping` denetler ve sonra geri arama kanalındaki yöntemi çağırır (bu `Ping` durumda, onay sayısı 1 ile karara göre belirlenirken özgün iletiyi göndermek için kullanılan kanaldır). Onay sayısı 0'a ulaştığında, yöntem döndürür ve tüm yanıtları aramayı başlatan istemci tarafından yapılan ilk çağrıya geri döndürür. <span data-ttu-id="4da42-115">Bu, geri arama uygulamasında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4da42-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Hem `Ping` yöntem `Pong` hem de yöntem istek/yanıt, bu `Ping` da ilk çağrının `CallbackChannel<T>.Pong()` geri dönene kadar geri dönülmediği anlamına gelir. İstemcide, `Pong` yöntem geri dönüş `Ping` yaptığı bir sonraki çağrıya kadar geri dönemez. <span data-ttu-id="4da42-118">Bekleyen isteği yanıtlayabilmesi için hem geri arama nın hem de hizmetin giden istek/yanıtlama çağrıları yapması gerektiğinden, her iki uygulamanın da ConcurrencyMode.Reentrant davranışıyla işaretlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4da42-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4da42-119">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4da42-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4da42-120">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="4da42-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4da42-121">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4da42-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4da42-122">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4da42-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4da42-123">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="4da42-123">Demonstrates</span></span>  
 <span data-ttu-id="4da42-124">Örneği çalıştırmak için istemci ve sunucu projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4da42-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="4da42-125">Ardından iki komut penceresi açın ve \<dizinleri örnek>\CS\Service\bin\debug ve \<örnek>\CS\Client\bin\debug dizinleri olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4da42-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="4da42-126">Ardından yazarak `service.exe` hizmeti başlatın ve giriş bağımsız değişkeni olarak geçirilen kenelerin başlangıç değeriyle Client.exe'yi çağırın.</span><span class="sxs-lookup"><span data-stu-id="4da42-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="4da42-127">10 kene için bir örnek çıktı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4da42-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="4da42-128">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="4da42-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4da42-129">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4da42-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4da42-130">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="4da42-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4da42-131">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="4da42-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
