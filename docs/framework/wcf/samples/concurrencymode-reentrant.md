---
title: ConcurrencyMode Yeniden Girme
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 0ac3b811c59abfbb3148ddad3d518443f7633adc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714960"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Yeniden Girme
Bu örnek, bir hizmet uygulamasında ConcurrencyMode. yeniden oluşturma kullanmanın zorunludur ve etkilerini gösterir. ConcurrencyMode. yeniden, hizmetin (veya geri aramanın) belirli bir zamanda yalnızca bir iletiyi (`ConcurencyMode.Single`benzer şekilde) işlediği anlamına gelir. Windows Communication Foundation (WCF), iş parçacığı güvenliğini sağlamak için bir iletiyi işlemek `InstanceContext` başka hiçbir ileti işlenemeyecektir. Yeniden eklenen modda `InstanceContext`, hizmetin bir sonraki çağrıya izin vermesini sağlamak için bir giden çağrı yapmadan önce, daha sonra bir sonraki çağrıya izin verirken (örnekte gösterilen şekilde yeniden eklenebilir), daha sonra, bir sonraki çağrıya bir dahaki sefer geldiğinde kilidi almak için, Davranışı göstermek için örnek, bir istemcinin ve hizmetin çift yönlü bir sözleşme kullanarak birbirleriyle nasıl ileti gönderebileceğini gösterir.  
  
 Tanımlanan sözleşme, hizmet tarafından uygulanan `Ping` yöntemi ve istemci tarafından uygulanan geri çağırma `Pong` yöntemi ile birlikte çift yönlü bir sözleşmedir. İstemci, bu çağrıyı başlatan bir değer sayısı ile sunucunun `Ping` yöntemini çağırır. Hizmet, değer sayısının 0 ' a eşit olup olmadığını denetler ve ardından değer sayısını azaltılarken geri çağırmaları `Pong` yöntemini çağırır. Bu, örnekte aşağıdaki kod tarafından yapılır.  
  
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
  
 Geri aramanın `Pong` uygulamasının `Ping` uygulamasıyla aynı mantığı vardır. Yani, değer sayısının sıfır olup olmadığını denetler ve ardından geri çağırma kanalında `Ping` yöntemini çağırır (Bu durumda, özgün `Ping` iletisini göndermek için kullanılan kanal budur), değer sayısı 1 ile azaltılır. Değer sayısının 0 ' a ulaştığı süre, yöntemi, çağrıyı başlatan istemci tarafından yapılan ilk çağrıya geri yanıt vermez. Bu, geri çağırma uygulamasında gösterilir.  
  
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
  
 Hem `Ping` hem de `Pong` yöntemleri istek/yanıt ' dir. Bu, `Ping` yapılan çağrının `CallbackChannel<T>.Pong()` dönüşene kadar döndürülmeyeceği anlamına gelir. İstemcide, `Pong` yöntemi döndürdüğü bir sonraki `Ping` çağrıya kadar dönemeyebilir. Hem geri çağırma hem de hizmetin bekleyen istek için yanıt vermeden önce giden istek/yanıt çağrıları yapması gerektiğinden, her iki uygulama da ConcurrencyMode. yeniden yer davranışıyla işaretlenmelidir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
## <a name="demonstrates"></a>Gösterir  
 Örneği çalıştırmak için, istemci ve sunucu projelerini derleyin. Sonra iki komut penceresi açın ve dizinleri \<örnek > \CS\Service\bin\debug ve \<örnek > \CS\Client\bin\debug dizinleriyle değiştirin. Ardından `service.exe` yazarak hizmeti başlatın ve ardından bir giriş bağımsız değişkeni olarak geçirilen işaret başlangıç değeriyle Client. exe dosyasını çağırın. 10 Ticks için örnek çıkış gösterilmektedir.  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
