---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 393c8a79cb60a33203b41a0778176a4d78a9b6ee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585317"
---
# <a name="concurrency"></a>Eşzamanlılık
Eşzamanlılık örneği, <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.ConcurrencyMode> bir hizmet örneğinin iletileri sıralı olarak veya aynı anda işleme gerekmediğini denetleyen, numaralandırma ile kullanımını gösterir. Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` . Bu örnek, ' den devralan yeni bir sözleşme tanımlar ve `ICalculatorConcurrency` `ICalculator` hizmet eşzamanlılık durumunu incelemek için iki ek işlem sağlar. Eşzamanlılık ayarını değiştirerek, istemcisini çalıştırarak davranış değişikliğini gözlemleyebilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Kullanılabilir üç eşzamanlılık modu vardır:  
  
- `Single`: Her hizmet örneği tek seferde bir ileti işler. Bu, varsayılan eşzamanlılık modudur.  
  
- `Multiple`: Her hizmet örneği aynı anda birden çok iletiyi işler. Bu eşzamanlılık modunu kullanabilmek için hizmet uygulamasının iş parçacığı açısından güvenli olması gerekir.  
  
- `Reentrant`: Her hizmet örneği tek seferde bir ileti işler, ancak yeniden geçen çağrıları kabul eder. Hizmet, bu çağrıyı yalnızca aradığında kabul eder. Yer, [ConcurrencyMode.](concurrencymode-reentrant.md) bir örnek örneğinde gösterilmiştir.  
  
 Eşzamanlılık kullanımı, örnek oluşturma moduyla ilgilidir. <xref:System.ServiceModel.InstanceContextMode.PerCall>Örnek olarak, her ileti yeni bir hizmet örneği tarafından işlendiği için eşzamanlılık ilgili değildir. Örnek olarak <xref:System.ServiceModel.InstanceContextMode.Single> , <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode.Multiple> tek örneğin iletileri sıralı veya eşzamanlı olarak işleme sunuluna bağlı olarak, ya da eşzamanlılık geçerlidir. <xref:System.ServiceModel.InstanceContextMode.PerSession>Örnek olarak, herhangi bir eşzamanlılık modu ilgili olabilir.  
  
 Service sınıfı, `[ServiceBehavior(ConcurrencyMode=<setting>)]` Aşağıdaki kod örneğinde gösterildiği gibi özniteliğiyle eşzamanlılık davranışını belirtir. Hangi satırların açıklama olarak değiştirilerek, `Single` ve `Multiple` eşzamanlılık modlarıyla denemeler yapabilirsiniz. Eşzamanlılık modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın.  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 Örnek, <xref:System.ServiceModel.ConcurrencyMode.Multiple> Varsayılan olarak örnek oluşturma ile eşzamanlılık kullanır <xref:System.ServiceModel.InstanceContextMode.Single> . İstemci kodu, zaman uyumsuz bir ara sunucu kullanacak şekilde değiştirilmiştir. Bu, istemcinin her bir çağrı arasında yanıt beklemeden hizmete birden çok çağrı yapmasına olanak sağlar. Hizmet eşzamanlılık modunun davranışındaki farkı gözlemleyebilirsiniz.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Hizmetin altında çalıştığı eşzamanlılık modu görüntülenir, her bir işlem çağrılır ve sonra işlem sayısı görüntülenir. Eşzamanlılık modu olduğunda `Multiple` , hizmet birden çok iletiyi eşzamanlı olarak işlediği için sonuçların nasıl çağrıldıklarından farklı bir sırada döndürüldiğine dikkat edin. Eşzamanlılık modunu olarak değiştirerek `Single` , hizmet her iletiyi sırayla işleyerek sonuçlar çağrıldıkları sırada döndürülür. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Proxy istemcisini oluşturmak için Svcutil. exe ' yi kullanırsanız, seçeneğini de bulundurtığınızdan emin olun `/async` .  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
