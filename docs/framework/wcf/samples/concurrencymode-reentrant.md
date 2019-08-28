---
title: ConcurrencyMode Yeniden Girme
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c6bb73957da055e9d867fbcb78ce78acdb8d0b76
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040135"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="0307b-102">ConcurrencyMode Yeniden Girme</span><span class="sxs-lookup"><span data-stu-id="0307b-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="0307b-103">Bu örnek, bir hizmet uygulamasında ConcurrencyMode. yeniden oluşturma kullanmanın zorunludur ve etkilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0307b-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="0307b-104">ConcurrencyMode. yeniden, hizmetin (veya geri aramanın) belirli bir zamanda yalnızca bir iletiyi (veya ' a benzer `ConcurencyMode.Single`) işleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0307b-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="0307b-105">Windows Communication Foundation (WCF), iş parçacığı güvenliğini sağlamak için ileti `InstanceContext` işlemeyi, başka hiçbir ileti işlenememesi için kilitler.</span><span class="sxs-lookup"><span data-stu-id="0307b-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="0307b-106">`InstanceContext` Yeniden kullanılabilir modda, hizmet bir sonraki çağrıya izin verirken bir giden çağrı yapmadan (örneğin, örnekte gösterilen şekilde yeniden eklenebilir), daha sonra, bu hizmete bir dahaki sefer daha sonra kilidi almak için bir giden çağrı yapmadan hemen önce kilidi açılır.</span><span class="sxs-lookup"><span data-stu-id="0307b-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="0307b-107">Davranışı göstermek için örnek, bir istemcinin ve hizmetin çift yönlü bir sözleşme kullanarak birbirleriyle nasıl ileti gönderebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0307b-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="0307b-108">Tanımlanan sözleşme, hizmet tarafından uygulanan `Ping` yönteme ve istemci tarafından uygulanan geri çağırma yöntemine `Pong` sahip bir çift yönlü sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="0307b-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="0307b-109">İstemci, çağrıyı başlatan bir değer `Ping` sayısı ile sunucunun yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0307b-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="0307b-110">Hizmet, değer sayısının 0 ' a eşit olup olmadığını denetler ve ardından değer sayısını azaltılarken `Pong` geri çağırmalar yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0307b-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="0307b-111">Bu, örnekte aşağıdaki kod tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="0307b-111">This is done by the following code in the sample.</span></span>  
  
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
  
 Geri çağırma `Pong` uygulamasının, `Ping` uygulamayla aynı mantığı vardır. Diğer bir deyişle, değer sayısının sıfır olup olmadığını denetler ve ardından geri çağırma kanalında `Ping` yöntemi çağırır (Bu durumda, özgün `Ping` iletiyi göndermek için kullanılan kanal budur), değer sayısı 1 ile azaltılır. Değer sayısının 0 ' a ulaştığı süre, yöntemi, çağrıyı başlatan istemci tarafından yapılan ilk çağrıya geri yanıt vermez. <span data-ttu-id="0307b-115">Bu, geri çağırma uygulamasında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0307b-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Ve yöntemlerinin her ikisi de istek/yanıt ' dir. Bu, öğesine `Ping` yapılan çağrı `CallbackChannel<T>.Pong()` geri dönene kadar geri dönmeyeceği anlamına gelir. `Pong` `Ping` İstemcide, `Pong` Yöntem döndürdüğü bir sonraki `Ping` çağrıya kadar dönemeyebilir. <span data-ttu-id="0307b-118">Hem geri çağırma hem de hizmetin bekleyen istek için yanıt vermeden önce giden istek/yanıt çağrıları yapması gerektiğinden, her iki uygulama da ConcurrencyMode. yeniden yer davranışıyla işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0307b-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0307b-119">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0307b-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0307b-120">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0307b-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0307b-121">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0307b-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0307b-122">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0307b-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0307b-123">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="0307b-123">Demonstrates</span></span>  
 <span data-ttu-id="0307b-124">Örneği çalıştırmak için, istemci ve sunucu projelerini derleyin.</span><span class="sxs-lookup"><span data-stu-id="0307b-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="0307b-125">Sonra iki komut penceresi açın ve dizinleri \<örnek > \CS\Service\bin\debug ve \<örnek > \CS\Client\bin\debug dizinleriyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0307b-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="0307b-126">Ardından yazarak `service.exe` hizmeti başlatın ve ardından bir giriş bağımsız değişkeni olarak geçirilen işaret başlangıç değeriyle Client. exe dosyasını çağırın.</span><span class="sxs-lookup"><span data-stu-id="0307b-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="0307b-127">10 Ticks için örnek çıkış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0307b-127">A sample output for 10 ticks is shown.</span></span>  
  
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
> <span data-ttu-id="0307b-128">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0307b-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0307b-129">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0307b-129">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="0307b-130">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="0307b-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0307b-131">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0307b-131">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
