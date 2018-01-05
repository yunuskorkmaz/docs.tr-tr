---
title: ConcurrencyMode Yeniden Girme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 450d47a9cdff709657458ed3fcc4b5948ccb960c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="eb8eb-102">ConcurrencyMode Yeniden Girme</span><span class="sxs-lookup"><span data-stu-id="eb8eb-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="eb8eb-103">Bu örnek, elde etmenizi ve bir hizmet uygulaması ConcurrencyMode.Reentrant kullanmanın etkileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="eb8eb-104">ConcurrencyMode.Reentrant gelir hizmetinin (veya geri çağırma) tek bir ileti belirli bir zamanda işleyen (benzer `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="eb8eb-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="eb8eb-105">İş parçacığı güvenliği sağlamak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kilitleri `InstanceContext` böylece başka iletiler işlenebilen bir ileti işleme.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-105">To ensure thread safety, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="eb8eb-106">Desteklemeyeceğini modu durumunda `InstanceContext` yalnızca hizmet (aşağıdaki örnekte gösterildiği gibi desteklemeyeceğini olabilir) sonraki çağrısını, böylece izin giden bir çağrı yapar önce kilidinin açık olduğundan bu geldiğinde hizmete sonraki zamanı kilidi elde etmek.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="eb8eb-107">Davranış göstermek için bir istemci ve hizmet iletileri birbirine çift yönlü sözleşme kullanma arasında nasıl gönderebilirsiniz örnek göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="eb8eb-108">Çift yönlü sözleşme ile tanımlanan sözleşme olan `Ping` hizmeti ve geri çağırma yöntemi tarafından uygulanan yöntemi `Pong` istemci tarafından uygulanan.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="eb8eb-109">Bir istemci sunucunun çağırır `Ping` yöntemi bir değer ile saymak böylece çağrı başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="eb8eb-110">Hizmet tık sayısı 0'a eşit değil geri çağırmalarını çalıştırır olup olmadığını denetler ve `Pong` yöntemi azaltma tık sayısı oluştu.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="eb8eb-111">Bu aşağıdaki örnek kodda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-111">This is done by the following code in the sample.</span></span>  
  
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
  
 Geri arama 's `Pong` uygulamaya sahip aynı mantığını `Ping` uygulaması. Diğer bir deyişle, bu değer sayısı sıfır değil sonra çağırır olup olmadığını denetler ve `Ping` geri çağırma kanalda yöntemi (Bu durumda, özgün göndermek için kullanılan kanal olduğu `Ping` ileti) ile değer 1 ile indirildiği sayısı. Böylece yöntem tık sayısı 0, ulaştığında şu anda geri çağrı başlatılan istemci tarafından yapılan ilk çağrıda tüm yanıtlar açmak. <span data-ttu-id="eb8eb-115">Bu geri çağırma uygulamasında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Hem `Ping` ve `Pong` yöntemleridir ilk çağrıda anlamına istek/yanıt `Ping` çağrısı kadar döndürmüyor `CallbackChannel<T>.Pong()` döndürür. İstemci üzerindeki `Pong` yöntemi kadar sonraki döndüremiyor `Ping` döndürür yapılan çağırın. <span data-ttu-id="eb8eb-118">Bekleyen isteği yanıtlayabilir önce geri çağırma ve hizmet istek/yanıt aramaların yapmalısınız çünkü her iki uygulamaları ConcurrencyMode.Reentrant davranışa işaretlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eb8eb-119">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="eb8eb-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eb8eb-120">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb8eb-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="eb8eb-121">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb8eb-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="eb8eb-122">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb8eb-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="eb8eb-123">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="eb8eb-123">Demonstrates</span></span>  
 <span data-ttu-id="eb8eb-124">Örneği çalıştırmak için istemci ve sunucu projeler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="eb8eb-125">Ardından iki komut penceresi açın ve dizinleri değiştirin \<örnek > \CS\Service\bin\debug ve \<örnek > \CS\Client\bin\debug dizinleri.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="eb8eb-126">Yazarak hizmeti başlatın `service.exe` ve giriş bağımsız değişken olarak geçirilen çizgilerine ilk değeri ile Client.exe çağırma.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="eb8eb-127">10 çizgilerine için örnek bir çıktı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-127">A sample output for 10 ticks is shown.</span></span>  
  
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
>  <span data-ttu-id="eb8eb-128">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eb8eb-129">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eb8eb-130">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb8eb-131">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a><span data-ttu-id="eb8eb-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb8eb-132">See Also</span></span>
