---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 1342e50a5dca56260f832f5e0d684f4f79d355e2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715996"
---
# <a name="concurrency"></a>Eşzamanlılık
Eşzamanlılık örneği, bir hizmet örneğinin iletileri sıralı veya eşzamanlı olarak işleme gerekmediğini denetleyen <xref:System.ServiceModel.ConcurrencyMode> numaralandırmada <xref:System.ServiceModel.ServiceBehaviorAttribute> kullanımını gösterir. Örnek, `ICalculator` hizmet sözleşmesini uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Bu örnek, `ICalculator`devralan `ICalculatorConcurrency`yeni bir sözleşme tanımlar ve hizmetin eşzamanlılık durumunu incelemek için iki ek işlem sağlar. Eşzamanlılık ayarını değiştirerek, istemcisini çalıştırarak davranış değişikliğini gözlemleyebilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Kullanılabilir üç eşzamanlılık modu vardır:  
  
- `Single`: her hizmet örneği tek seferde bir ileti işler. Bu, varsayılan eşzamanlılık modudur.  
  
- `Multiple`: her hizmet örneği aynı anda birden çok iletiyi işler. Bu eşzamanlılık modunu kullanabilmek için hizmet uygulamasının iş parçacığı açısından güvenli olması gerekir.  
  
- `Reentrant`: her hizmet örneği tek seferde bir ileti işler, ancak yeniden geçen çağrıları kabul eder. Hizmet, bu çağrıyı yalnızca aradığında kabul eder. Yer, [ConcurrencyMode.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) bir örnek örneğinde gösterilmiştir.  
  
 Eşzamanlılık kullanımı, örnek oluşturma moduyla ilgilidir. <xref:System.ServiceModel.InstanceContextMode.PerCall> örnek oluşturma, her ileti yeni bir hizmet örneği tarafından işlendiği için eşzamanlılık ilgili değildir. <xref:System.ServiceModel.InstanceContextMode.Single> örnek oluşturma bölümünde, tek örneğin iletileri sıralı veya eşzamanlı olarak işleme sunuluna bağlı olarak, <xref:System.ServiceModel.ConcurrencyMode.Single> veya <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık geçerlidir. <xref:System.ServiceModel.InstanceContextMode.PerSession> örnek oluşturma bölümünde eşzamanlılık modlarından herhangi biri ilgili olabilir.  
  
 Service sınıfı, aşağıdaki kod örneğinde gösterildiği gibi `[ServiceBehavior(ConcurrencyMode=<setting>)]` özniteliğiyle eşzamanlılık davranışını belirtir. Hangi satırların açıklama olarak değiştirilerek `Single` ve `Multiple` eşzamanlılık modlarını deneyebilirsiniz. Eşzamanlılık modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın.  
  
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
  
 Örnek, varsayılan olarak <xref:System.ServiceModel.InstanceContextMode.Single> örnekleyerek <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık kullanır. İstemci kodu, zaman uyumsuz bir ara sunucu kullanacak şekilde değiştirilmiştir. Bu, istemcinin her bir çağrı arasında yanıt beklemeden hizmete birden çok çağrı yapmasına olanak sağlar. Hizmet eşzamanlılık modunun davranışındaki farkı gözlemleyebilirsiniz.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Hizmetin altında çalıştığı eşzamanlılık modu görüntülenir, her bir işlem çağrılır ve sonra işlem sayısı görüntülenir. Eşzamanlılık modu `Multiple`olduğunda, hizmet birden çok iletiyi eşzamanlı olarak işlediği için sonuçların nasıl çağrıldıklarından farklı bir sırada döndürüldiğine dikkat edin. Eşzamanlılık modunu `Single`olarak değiştirerek, hizmet her iletiyi sırayla işleyerek sonuçlar çağrıldıkları sırada döndürülür. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Proxy istemcisini oluşturmak için Svcutil. exe ' yi kullanırsanız, `/async` seçeneğini de bulundurtığınızdan emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
