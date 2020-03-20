---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183940"
---
# <a name="concurrency"></a>Eşzamanlılık
Eşzamanlılık örneği, bir <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmetin <xref:System.ServiceModel.ConcurrencyMode> bir örneğinin iletileri sırayla mı yoksa aynı anda mı işlediğini kontrol eden numaralandırma ile birlikte kullanılmasını gösterir. Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır. Bu örnek, `ICalculatorConcurrency`hizmet eşzamanlılık durumunu denetlemek `ICalculator`için iki ek işlem sağlayan, devralan yeni bir sözleşme tanımlar. Eşzamanlılık ayarını değiştirerek, istemciyi çalıştırarak davranış değişikliğini gözlemleyebilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Üç eşzamanlılık modu vardır:  
  
- `Single`: Her hizmet örneği aynı anda bir iletiyi işler. Bu varsayılan eşzamanlılık modudur.  
  
- `Multiple`: Her hizmet örneği aynı anda birden çok iletiyi işler. Bu eşzamanlılık modunu kullanmak için hizmet uygulaması iş parçacığı güvenli olmalıdır.  
  
- `Reentrant`: Her hizmet örneği aynı anda bir iletiyi işler, ancak reentrant çağrılarını kabul eder. Hizmet bu çağrıları yalnızca çağrı yaparken kabul eder. Reentrant [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) örnek gösterilmiştir.  
  
 Eşzamanlılık kullanımı instancing modu ile ilgilidir. Her <xref:System.ServiceModel.InstanceContextMode.PerCall> ileti yeni bir hizmet örneği tarafından işlendiğinden, eşzamanlılık instancing olarak ilgili değildir. Tek <xref:System.ServiceModel.InstanceContextMode.Single> bir örneğin iletileri <xref:System.ServiceModel.ConcurrencyMode.Multiple> sırayla mı yoksa eş zamanlı olarak mı işlediğine bağlı olarak, instancing olarak, ya da <xref:System.ServiceModel.ConcurrencyMode.Single> eşzamanlılık önemlidir. Instancing <xref:System.ServiceModel.InstanceContextMode.PerSession> olarak, eşzamanlılık modları herhangi ilgili olabilir.  
  
 Hizmet sınıfı, öznitelik ile `[ServiceBehavior(ConcurrencyMode=<setting>)]` eşzamanlılık davranışını aşağıdaki kod örneğinde gösterildiği gibi belirtir. Hangi satırların yorumlanabileceğini değiştirerek, `Single` eşzamanlılık modlarını deneyebilirsiniz. `Multiple` Eşzamanlılık modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın.  
  
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
  
 Örnek temerrüt <xref:System.ServiceModel.InstanceContextMode.Single> tarafından instancing ile eşzamanlılık kullanır. <xref:System.ServiceModel.ConcurrencyMode.Multiple> İstemci kodu eşzamanlı proxy kullanmak üzere değiştirildi. Bu, istemcinin her arama arasında yanıt beklemeden hizmete birden çok arama yapmasına olanak tanır. Hizmet eşzamanlılık modunun davranışındaki farkı gözlemleyebilirsiniz.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Hizmetin altında çalıştırdığı eşzamanlılık modu görüntülenir, her işlem çağrılır ve işlem sayısı görüntülenir. Eşzamanlılık modu `Multiple`olduğunda, hizmet aynı anda birden çok iletiyi işlediği için, sonuçların çağrıldıkları şekilden farklı bir sırada döndürüldüye dikkat edin. Eşzamanlılık modunu `Single`değiştirerek, her iletiyi sırayla işler, çünkü hizmet çağrıldıkları sırada döndürülür. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Proxy istemcisini oluşturmak için Svcutil.exe kullanıyorsanız, `/async` seçeneği eklediğinizden emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
