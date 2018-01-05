---
title: "Eşzamanlılık"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c63882055718bd54d1983ea0aa10d208bd70793f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="concurrency"></a>Eşzamanlılık
Eşzamanlılık örneği kullanmayı göstermektedir <xref:System.ServiceModel.ServiceBehaviorAttribute> ile <xref:System.ServiceModel.ConcurrencyMode> bir hizmet örneği iletilerin sıralı olarak veya aynı anda işler olup olmadığını denetler numaralandırması. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme. Bu örnek yeni bir sözleşme tanımlar `ICalculatorConcurrency`, devralan `ICalculator`, hizmet eşzamanlılık durumunu incelemek için iki ek işlem sağlama. Eşzamanlılık ayarı değiştirerek istemci çalıştırarak davranışında değişiklik görebilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Üç eşzamanlılık modu vardır:  
  
-   `Single`: Her hizmet örneği aynı anda tek bir ileti işler. Varsayılan eşzamanlılık modu budur.  
  
-   `Multiple`: Her hizmet örneği aynı anda birden fazla ileti işler. Hizmet uygulaması bu eşzamanlılık modunu kullanmak için iş parçacığı açısından güvenli olması gerekir.  
  
-   `Reentrant`: Her hizmet örneği aynı anda tek bir ileti işler, ancak desteklemeyeceğini çağrılarını kabul eder. Bunu çağrılırken sırasında hizmet yalnızca bu çağrıları kabul eder. Yeniden girme gösterilmiştir [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) örnek.  
  
 Eşzamanlılık kullanımını örnekleme modunu ilişkilidir. İçinde <xref:System.ServiceModel.InstanceContextMode.PerCall> yeni bir hizmet örneği tarafından işlenen her iletisi depolamasına, eşzamanlılık ilgili değil. İçinde <xref:System.ServiceModel.InstanceContextMode.Single> depolamasına, ya da <xref:System.ServiceModel.ConcurrencyMode.Single> veya <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık olup tek örnek iletilerin sıralı olarak veya aynı anda işler bağlı olarak ilgili. İçinde <xref:System.ServiceModel.InstanceContextMode.PerSession> depolamasına, herhangi bir eşzamanlılık modu uygun olabilir.  
  
 Hizmet sınıfı ile eşzamanlılık davranışını belirten `[ServiceBehavior(ConcurrencyMode=<setting>)]` özniteliği aşağıdaki kod örneğinde gösterildiği gibi. Hangi satırların kılınmıştır değiştirerek deneme yapabileceğiniz `Single` ve `Multiple` eşzamanlılık modu. Eşzamanlılık modu değiştirdikten sonra hizmeti yeniden unutmayın.  
  
```  
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
  
 Örnek kullanır <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık ile <xref:System.ServiceModel.InstanceContextMode.Single> varsayılan örnek oluşturma. Zaman uyumsuz bir proxy kullanmak için istemci kodu değiştirildi. Bu her çağrı arasında bir yanıt beklemeden hizmetin birden fazla çağrı yapmak istemcinin sağlar. Hizmet eşzamanlılık modu davranışını farkı görebilirsiniz.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Hizmetin çalıştığı eşzamanlılık modu görüntülenir, her işlem çağrılır ve sonra işlem sayısını görüntülenir. Eşzamanlılık modunda olduğunda dikkat `Multiple`nasıl adı veriliyordu olandan farklı bir sırada sonuçların döndürülmesini, hizmet işlediğinden birden çok eşzamanlı olarak iletileri. Eşzamanlılık modu değiştirerek `Single`, hizmetin her ileti sıralı olarak işlediğinden sonuçlar bunlar olarak adlandırılan, sırayla döndürülür. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Proxy istemcisi oluşturmak için Svcutil.exe kullanırsanız, eklediğinizden emin olun `/async` seçeneği.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a>Ayrıca Bkz.
