---
title: ConcurrencyMode Yeniden Girme
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c5fa690ca3b8ffe14eb9f19f0bb096b867ab992f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740535"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="58f05-102">ConcurrencyMode Yeniden Girme</span><span class="sxs-lookup"><span data-stu-id="58f05-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="58f05-103">Bu örnek, bir hizmet uygulamasına ConcurrencyMode.Reentrant kullanmanın etkileri ve gerekliliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="58f05-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="58f05-104">ConcurrencyMode.Reentrant gelir hizmet (veya geri çağırma) belirli bir zamanda yalnızca bir ileti işler (alınmak üzere `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="58f05-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="58f05-105">İş parçacığı güvenliği sağlamak için Windows Communication Foundation (WCF) kilitler `InstanceContext` ileti işlenirken, böylece başka iletiler işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="58f05-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="58f05-106">Yeniden girilen modu durumunda `InstanceContext` yalnızca hizmet böylece (Bu örnekte gösterildiği gibi yeniden girilen olabilir) sonraki çağrı izin vererek giden bir çağrı yapmadan önce açılmış devamlı hizmete bir sonraki sefer kilidi almak için.</span><span class="sxs-lookup"><span data-stu-id="58f05-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="58f05-107">Davranış göstermek için nasıl hizmet ve istemci arasında çift yönlü sözleşme kullanarak birbirlerinin iletiler gönderebilir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="58f05-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="58f05-108">Çift yönlü sözleşme ile tanımlanan sözleşme olan `Ping` hizmet ve geri çağırma yöntemi tarafından uygulanan yöntem `Pong` istemci tarafından uygulanan.</span><span class="sxs-lookup"><span data-stu-id="58f05-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="58f05-109">Bir istemci sunucunun çağırır `Ping` yöntemi ile bir onay sayısı böylece çağrı başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="58f05-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="58f05-110">Hizmet, işaret sayısını 0'a eşit değil ve ardından geri çağırmalarını çalıştırır denetler `Pong` yöntemi işaret sayısını azaltma oluştu.</span><span class="sxs-lookup"><span data-stu-id="58f05-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="58f05-111">Bu, aşağıdaki kod örneğinde tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="58f05-111">This is done by the following code in the sample.</span></span>  
  
```  
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
  
 Geri çağırma'nın `Pong` aynı mantığı uygulamasına sahip `Ping` uygulaması. Diğer bir deyişle, işaret sayısı sıfır değil ve ardından çağırır denetler `Ping` yöntemi geri çağırma kanalındaki (Bu durumda, özgün göndermek için kullanılan kanal olduğu `Ping` ileti) 1 ile değer çizgisi indirildiği sayısı. İşaret sayısını 0, böylece döner ulaştığında şu geri çağrı başlatılan istemci tarafından yapılan ilk çağrı tüm yanıtlar çözülme. <span data-ttu-id="58f05-115">Bu geri çağırma uygulamasında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="58f05-115">This is shown in the callback implementation.</span></span>  
  
```  
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
  
 Hem `Ping` ve `Pong` yöntemlerdir yapılan ilk çağrı anlamına istek/yanıt `Ping` çağrısına kadar döndürmeyen `CallbackChannel<T>.Pong()` döndürür. İstemci üzerindeki `Pong` metodu gelecek kadar döndüremiyor `Ping` döndürür yapılan çağırın. <span data-ttu-id="58f05-118">Bekleyen istek için yanıt verebilir önce geri çağırma hem hizmet aramaların istek/yanıt vermeniz gerekir çünkü her iki uygulamaları ConcurrencyMode.Reentrant davranışı ile işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="58f05-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58f05-119">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="58f05-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="58f05-120">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58f05-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="58f05-121">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58f05-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="58f05-122">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58f05-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="58f05-123">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="58f05-123">Demonstrates</span></span>  
 <span data-ttu-id="58f05-124">Örneği çalıştırmak için istemci ve sunucu projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58f05-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="58f05-125">Ardından iki komut penceresi açın ve dizinleri \<örnek > \CS\Service\bin\debug ve \<örnek > \CS\Client\bin\debug dizinleri.</span><span class="sxs-lookup"><span data-stu-id="58f05-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="58f05-126">Yazarak hizmeti başlatın `service.exe` ve Client.exe işareti giriş bağımsız değişken olarak geçirilen ilk değerle'ı çağırın.</span><span class="sxs-lookup"><span data-stu-id="58f05-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="58f05-127">10 saat döngüsü için örnek çıktı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58f05-127">A sample output for 10 ticks is shown.</span></span>  
  
```  
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
>  <span data-ttu-id="58f05-128">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="58f05-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58f05-129">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="58f05-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="58f05-130">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="58f05-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58f05-131">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="58f05-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a><span data-ttu-id="58f05-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58f05-132">See Also</span></span>
