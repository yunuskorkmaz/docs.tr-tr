---
title: ConcurrencyMode Yeniden Girme
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 15edc89934bb105772144820a07991e77d15be62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199966"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Yeniden Girme
Bu örnek, bir hizmet uygulamasına ConcurrencyMode.Reentrant kullanmanın etkileri ve gerekliliğini gösterir. ConcurrencyMode.Reentrant gelir hizmet (veya geri çağırma) belirli bir zamanda yalnızca bir ileti işler (alınmak üzere `ConcurencyMode.Single`). İş parçacığı güvenliği sağlamak için Windows Communication Foundation (WCF) kilitler `InstanceContext` ileti işlenirken, böylece başka iletiler işlenebilir. Yeniden girilen modu durumunda `InstanceContext` yalnızca hizmet böylece (Bu örnekte gösterildiği gibi yeniden girilen olabilir) sonraki çağrı izin vererek giden bir çağrı yapmadan önce açılmış devamlı hizmete bir sonraki sefer kilidi almak için. Davranış göstermek için nasıl hizmet ve istemci arasında çift yönlü sözleşme kullanarak birbirlerinin iletiler gönderebilir örnek gösterir.  
  
 Çift yönlü sözleşme ile tanımlanan sözleşme olan `Ping` hizmet ve geri çağırma yöntemi tarafından uygulanan yöntem `Pong` istemci tarafından uygulanan. Bir istemci sunucunun çağırır `Ping` yöntemi ile bir onay sayısı böylece çağrı başlatılıyor. Hizmet, işaret sayısını 0'a eşit değil ve ardından geri çağırmalarını çalıştırır denetler `Pong` yöntemi işaret sayısını azaltma oluştu. Bu, aşağıdaki kod örneğinde tarafından gerçekleştirilir.  
  
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
  
 Geri çağırma'nın `Pong` aynı mantığı uygulamasına sahip `Ping` uygulaması. Diğer bir deyişle, işaret sayısı sıfır değil ve ardından çağırır denetler `Ping` yöntemi geri çağırma kanalındaki (Bu durumda, özgün göndermek için kullanılan kanal olduğu `Ping` ileti) 1 ile değer çizgisi indirildiği sayısı. İşaret sayısını 0, böylece döner ulaştığında şu geri çağrı başlatılan istemci tarafından yapılan ilk çağrı tüm yanıtlar çözülme. Bu geri çağırma uygulamasında gösterilir.  
  
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
  
 Hem `Ping` ve `Pong` yöntemlerdir yapılan ilk çağrı anlamına istek/yanıt `Ping` çağrısına kadar döndürmeyen `CallbackChannel<T>.Pong()` döndürür. İstemci üzerindeki `Pong` metodu gelecek kadar döndüremiyor `Ping` döndürür yapılan çağırın. Bekleyen istek için yanıt verebilir önce geri çağırma hem hizmet aramaların istek/yanıt vermeniz gerekir çünkü her iki uygulamaları ConcurrencyMode.Reentrant davranışı ile işaretlenmelidir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Gösteriler  
 Örneği çalıştırmak için istemci ve sunucu projeleri oluşturun. Ardından iki komut penceresi açın ve dizinleri \<örnek > \CS\Service\bin\debug ve \<örnek > \CS\Client\bin\debug dizinleri. Yazarak hizmeti başlatın `service.exe` ve Client.exe işareti giriş bağımsız değişken olarak geçirilen ilk değerle'ı çağırın. 10 saat döngüsü için örnek çıktı gösterilmektedir.  
  
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
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
