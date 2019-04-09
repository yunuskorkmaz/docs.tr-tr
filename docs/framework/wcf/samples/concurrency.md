---
title: Eşzamanlılık
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: f0d4996a7ea8ab49df780635127f39064b1050c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119151"
---
# <a name="concurrency"></a>Eşzamanlılık
Eşzamanlılık örneği kullanmayı gösterir <xref:System.ServiceModel.ServiceBehaviorAttribute> ile <xref:System.ServiceModel.ConcurrencyMode> sabit listesi bir hizmet örneği sırayla veya aynı anda iletileri işleyen olup olmadığını denetler. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi. Bu örnek yeni bir sözleşme tanımlayan `ICalculatorConcurrency`, işlevinden devralan `ICalculator`, hizmet eşzamanlılık durumunu incelemek için iki ek işlemler sağlar. Eş zamanlılık ayarı değiştirerek istemci çalıştırarak davranış değişikliği görebilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Üç eşzamanlılık modu vardır:  
  
-   `Single`: Her hizmet örneği aynı anda tek bir ileti işler. Varsayılan eşzamanlılık modu budur.  
  
-   `Multiple`: Her hizmet örneği birden çok iletiyi eş zamanlı olarak işler. Hizmet uygulaması bu eşzamanlılık modu kullanmak için iş parçacığı açısından güvenli olması gerekir.  
  
-   `Reentrant`: Her hizmet örneği, tek bir ileti işler, ancak desteklemeyeceğini çağrılarını kabul eder. Bunu çağırma yaparken hizmeti yalnızca bu çağrıları kabul eder. ConcurrencyMode için Reentrant gösterilmiştir [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) örnek.  
  
 Eşzamanlılık kullanımını örneklemesini moduna ilişkilidir. İçinde <xref:System.ServiceModel.InstanceContextMode.PerCall> yeni bir hizmet örneği tarafından işlenen her iletisi depolamasına, eşzamanlılık ilgili değildir, çünkü. İçinde <xref:System.ServiceModel.InstanceContextMode.Single> depolamasına, ya da <xref:System.ServiceModel.ConcurrencyMode.Single> veya <xref:System.ServiceModel.ConcurrencyMode.Multiple> olup olmadığı tek örnekli iletileri sırayla veya aynı anda işler bağlı olarak, ilgili eşzamanlılık. İçinde <xref:System.ServiceModel.InstanceContextMode.PerSession> depolamasına, eşzamanlılık modun herhangi birinde uygun olabilir.  
  
 Hizmet sınıfı ile eşzamanlılık davranışı belirtir `[ServiceBehavior(ConcurrencyMode=<setting>)]` özniteliği aşağıdaki kod örneğinde gösterildiği gibi. Hangi satırlar açıklama satırlarıdır değiştirerek deneme yapabileceğiniz `Single` ve `Multiple` eşzamanlılık modu. Eşzamanlılık modu değiştirdikten sonra hizmeti yeniden unutmayın.  
  
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
  
 Örnek kullanır <xref:System.ServiceModel.ConcurrencyMode.Multiple> eşzamanlılık ile <xref:System.ServiceModel.InstanceContextMode.Single> varsayılan örnek oluşturma. İstemci kodu, zaman uyumsuz bir ara sunucusunu kullanacak şekilde değiştirildi. Bu, istemci arasındaki her çağrı bir yanıt beklemeden birden çok hizmete çağrı yapma sağlar. Hizmet eşzamanlılık modu davranıştaki farkı görebilirsiniz.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Hizmetinin altında çalışmakta olduğu eşzamanlılık modu görüntülenir, her işlem çağrılır ve sonra işlem sayısını görüntülenir. Eşzamanlılık modu olduğunda dikkat `Multiple`nasıl çağrılan daha farklı bir sırada döndürülen sonuçları, hizmet işlediğinden birden çok eşzamanlı olarak iletileri. İçin eşzamanlılık modu değiştirerek `Single`, hizmetin her ileti sıralı olarak işlediğinden, sonuçları çağrılır, sırayla döndürülür. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Proxy istemcisi üretmek için Svcutil.exe kullanma eklediğinizden emin olun `/async` seçeneği.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
