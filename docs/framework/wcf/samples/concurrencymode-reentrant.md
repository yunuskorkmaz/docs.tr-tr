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
ms.openlocfilehash: bf852c67bec8abb2af3593d537010e5cc2718176
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Yeniden Girme
Bu örnek, elde etmenizi ve bir hizmet uygulaması ConcurrencyMode.Reentrant kullanmanın etkileri gösterir. ConcurrencyMode.Reentrant gelir hizmetinin (veya geri çağırma) tek bir ileti belirli bir zamanda işleyen (benzer `ConcurencyMode.Single`). İş parçacığı güvenliği sağlamak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kilitleri `InstanceContext` böylece başka iletiler işlenebilen bir ileti işleme. Desteklemeyeceğini modu durumunda `InstanceContext` yalnızca hizmet (aşağıdaki örnekte gösterildiği gibi desteklemeyeceğini olabilir) sonraki çağrısını, böylece izin giden bir çağrı yapar önce kilidinin açık olduğundan bu geldiğinde hizmete sonraki zamanı kilidi elde etmek. Davranış göstermek için bir istemci ve hizmet iletileri birbirine çift yönlü sözleşme kullanma arasında nasıl gönderebilirsiniz örnek göstermektedir.  
  
 Çift yönlü sözleşme ile tanımlanan sözleşme olan `Ping` hizmeti ve geri çağırma yöntemi tarafından uygulanan yöntemi `Pong` istemci tarafından uygulanan. Bir istemci sunucunun çağırır `Ping` yöntemi bir değer ile saymak böylece çağrı başlatılıyor. Hizmet tık sayısı 0'a eşit değil geri çağırmalarını çalıştırır olup olmadığını denetler ve `Pong` yöntemi azaltma tık sayısı oluştu. Bu aşağıdaki örnek kodda gerçekleştirilir.  
  
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
  
 Geri arama 's `Pong` uygulamaya sahip aynı mantığını `Ping` uygulaması. Diğer bir deyişle, bu değer sayısı sıfır değil sonra çağırır olup olmadığını denetler ve `Ping` geri çağırma kanalda yöntemi (Bu durumda, özgün göndermek için kullanılan kanal olduğu `Ping` ileti) ile değer 1 ile indirildiği sayısı. Böylece yöntem tık sayısı 0, ulaştığında şu anda geri çağrı başlatılan istemci tarafından yapılan ilk çağrıda tüm yanıtlar açmak. Bu geri çağırma uygulamasında gösterilir.  
  
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
  
 Hem `Ping` ve `Pong` yöntemleridir ilk çağrıda anlamına istek/yanıt `Ping` çağrısı kadar döndürmüyor `CallbackChannel<T>.Pong()` döndürür. İstemci üzerindeki `Pong` yöntemi kadar sonraki döndüremiyor `Ping` döndürür yapılan çağırın. Bekleyen isteği yanıtlayabilir önce geri çağırma ve hizmet istek/yanıt aramaların yapmalısınız çünkü her iki uygulamaları ConcurrencyMode.Reentrant davranışa işaretlenmesi gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Gösteriler  
 Örneği çalıştırmak için istemci ve sunucu projeler oluşturun. Ardından iki komut penceresi açın ve dizinleri değiştirin \<örnek > \CS\Service\bin\debug ve \<örnek > \CS\Client\bin\debug dizinleri. Yazarak hizmeti başlatın `service.exe` ve giriş bağımsız değişken olarak geçirilen çizgilerine ilk değeri ile Client.exe çağırma. 10 çizgilerine için örnek bir çıktı gösterilir.  
  
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
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a>Ayrıca Bkz.
