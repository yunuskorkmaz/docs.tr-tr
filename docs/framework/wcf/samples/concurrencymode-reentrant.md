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
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Yeniden Girme
Bu örnek, concurrencyMode.Reentrant'ı bir hizmet uygulamasında kullanmanın gerekliliğini ve sonuçlarını göstermektedir. ConcurrencyMode.Reentrant, hizmetin (veya geri aramanın) belirli bir zamanda yalnızca `ConcurencyMode.Single`bir iletiyi işlediğini (benzer şekilde) ifade eder. İş parçacığı güvenliğini sağlamak için, Windows Communication `InstanceContext` Foundation (WCF) başka iletilerin işlenememesi için bir iletiyi işlemeyi kilitler. Reentrant modu durumunda, `InstanceContext` hizmet böylece sonraki arama, (örnek gösterildiği gibi reentrant olabilir) hizmete bir dahaki sefere kilit almak için izin giden bir arama yapmadan hemen önce kilidi açılır. Davranışı göstermek için örnek, istemci ve hizmetin çift yönlü bir sözleşme kullanarak birbirleri arasında nasıl ileti gönderebileceğini gösterir.  
  
 Tanımlanan sözleşme, hizmet tarafından uygulanan `Ping` yöntem ve istemci tarafından uygulanan geri `Pong` arama yöntemi ile çift yönlü bir sözleşmedir. İstemci, sunucunun `Ping` yöntemini kene sayısıyla çağırır ve ardından aramayı başlatır. Hizmet, onay sayısının 0'a eşit olup olmadığını denetler `Pong` ve onay sayısını azalırken geri arama yöntemini çağırır. Bu, örnekteki aşağıdaki kod tarafından yapılır.  
  
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
  
 Geri aramanın `Pong` `Ping` uygulaması, uygulamayla aynı mantığa sahiptir. Diğer bir deyişle, onay sayısının sıfır olup olmadığını `Ping` denetler ve sonra geri arama kanalındaki yöntemi çağırır (bu `Ping` durumda, onay sayısı 1 ile karara göre belirlenirken özgün iletiyi göndermek için kullanılan kanaldır). Onay sayısı 0'a ulaştığında, yöntem döndürür ve tüm yanıtları aramayı başlatan istemci tarafından yapılan ilk çağrıya geri döndürür. Bu, geri arama uygulamasında gösterilir.  
  
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
  
 Hem `Ping` yöntem `Pong` hem de yöntem istek/yanıt, bu `Ping` da ilk çağrının `CallbackChannel<T>.Pong()` geri dönene kadar geri dönülmediği anlamına gelir. İstemcide, `Pong` yöntem geri dönüş `Ping` yaptığı bir sonraki çağrıya kadar geri dönemez. Bekleyen isteği yanıtlayabilmesi için hem geri arama nın hem de hizmetin giden istek/yanıtlama çağrıları yapması gerektiğinden, her iki uygulamanın da ConcurrencyMode.Reentrant davranışıyla işaretlemesi gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
## <a name="demonstrates"></a>Gösteriler  
 Örneği çalıştırmak için istemci ve sunucu projeleri oluşturun. Ardından iki komut penceresi açın ve \<dizinleri örnek>\CS\Service\bin\debug ve \<örnek>\CS\Client\bin\debug dizinleri olarak değiştirin. Ardından yazarak `service.exe` hizmeti başlatın ve giriş bağımsız değişkeni olarak geçirilen kenelerin başlangıç değeriyle Client.exe'yi çağırın. 10 kene için bir örnek çıktı gösterilir.  
  
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
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
