---
title: Örnek Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 2fb48ee413c48f481b433f58352c2d0fe38f3972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503891"
---
# <a name="instancing"></a>Örnek Oluşturma
Instancing örnek istemci isteklerine yanıt olarak bir hizmet sınıfın örnekleri nasıl oluşturulduğunu denetimleri örneklemesini davranışı ayarını gösterir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme. Bu örnek yeni bir sözleşme tanımlar `ICalculatorInstance`, devralan `ICalculator`. Tarafından belirtilen sözleşme `ICalculatorInstance` hizmet örneği durumunu incelemek için üç ek işlemler sağlar. Örneklemesini ayarı değiştirerek istemci çalıştırarak davranışında değişiklik görebilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Aşağıdaki örneklemesini modları kullanılabilir:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Yeni bir hizmet örneği, her istemci isteği için oluşturulur.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Yeni bir örneğini, her yeni istemci oturumu için oluşturulur ve bu oturuma (oturum destekleyen bir bağlama gerektirir) ömrü boyunca saklanır.  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Bir hizmet sınıfında tek bir örnek uygulama ömrü boyunca tüm istemci isteklerini işler.  
  
 Hizmet sınıfı ile örneklemesini davranışını belirten `[ServiceBehavior(InstanceContextMode=<setting>)]` özniteliği aşağıdaki kod örneğinde gösterildiği gibi. Hangi satırların değiştirerek geçersiz kılınan çıkışı, her bir örneği modları davranış gözlenir. Örnekleme modunu değiştirdikten sonra hizmeti yeniden unutmayın. İstemcide belirtmek için örnek oluşturma ile ilgili ayar yok.  
  
```  
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Hizmetinin altında çalışan örnek modu görüntülenir. Her işleminden sonra örnek kimliği ve işlem sayısı örnekleme modunu davranışını yansıtacak şekilde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
  
## <a name="see-also"></a>Ayrıca Bkz.
