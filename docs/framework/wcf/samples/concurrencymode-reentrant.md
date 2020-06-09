---
title: ConcurrencyMode Yeniden Girme
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 67e719afd40b52f37c777cf9791291a16878592f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600094"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Yeniden Girme
Bu örnek, bir hizmet uygulamasında ConcurrencyMode. yeniden oluşturma kullanmanın zorunludur ve etkilerini gösterir. ConcurrencyMode. yeniden, hizmetin (veya geri aramanın) belirli bir zamanda yalnızca bir iletiyi (veya ' a benzer) Işleyeceğini belirtir `ConcurencyMode.Single` . Windows Communication Foundation (WCF), iş parçacığı güvenliğini sağlamak için `InstanceContext` ileti işlemeyi, başka hiçbir ileti işlenememesi için kilitler. `InstanceContext`Yeniden kullanılabilir modda, hizmet bir sonraki çağrıya izin verirken bir giden çağrı yapmadan (örneğin, örnekte gösterilen şekilde yeniden eklenebilir), daha sonra, bu hizmete bir dahaki sefer daha sonra kilidi almak için bir giden çağrı yapmadan hemen önce kilidi açılır. Davranışı göstermek için örnek, bir istemcinin ve hizmetin çift yönlü bir sözleşme kullanarak birbirleriyle nasıl ileti gönderebileceğini gösterir.  
  
 Tanımlanan sözleşme, `Ping` hizmet tarafından uygulanan yönteme ve istemci tarafından uygulanan geri çağırma yöntemine sahip bir çift yönlü sözleşmedir `Pong` . İstemci, `Ping` çağrıyı başlatan bir değer sayısı ile sunucunun yöntemini çağırır. Hizmet, değer sayısının 0 ' a eşit olup olmadığını denetler ve ardından `Pong` değer sayısını azaltılarken geri çağırmalar yöntemini çağırır. Bu, örnekte aşağıdaki kod tarafından yapılır.  
  
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
  
 Geri çağırma `Pong` uygulamasının, uygulamayla aynı mantığı vardır `Ping` . Diğer bir deyişle, değer sayısının sıfır olup olmadığını denetler ve ardından `Ping` geri çağırma kanalında yöntemi çağırır (Bu durumda, özgün iletiyi göndermek için kullanılan kanal budur `Ping` ), değer sayısı 1 ile azaltılır. Değer sayısının 0 ' a ulaştığı süre, yöntemi, çağrıyı başlatan istemci tarafından yapılan ilk çağrıya geri yanıt vermez. Bu, geri çağırma uygulamasında gösterilir.  
  
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
  
 Ve yöntemlerinin her ikisi de `Ping` `Pong` istek/yanıt ' dir. Bu, öğesine yapılan `Ping` çağrı geri dönene kadar geri dönmeyeceği anlamına gelir `CallbackChannel<T>.Pong()` . İstemcide, `Pong` Yöntem döndürdüğü bir sonraki çağrıya kadar dönemeyebilir `Ping` . Hem geri çağırma hem de hizmetin bekleyen istek için yanıt vermeden önce giden istek/yanıt çağrıları yapması gerektiğinden, her iki uygulama da ConcurrencyMode. yeniden yer davranışıyla işaretlenmelidir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
## <a name="demonstrates"></a>Gösteriler  
 Örneği çalıştırmak için, istemci ve sunucu projelerini derleyin. Sonra iki komut penceresi açın ve dizinleri \<sample> \Cs\service\bin\debug ve \<sample> \Cs\client\bin\debug dizinleriyle değiştirin. Ardından yazarak hizmeti başlatın `service.exe` ve ardından bir giriş bağımsız değişkeni olarak geçirilen işaret başlangıç değeriyle Client. exe dosyasını çağırın. 10 Ticks için örnek çıkış gösterilmektedir.  
  
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
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
