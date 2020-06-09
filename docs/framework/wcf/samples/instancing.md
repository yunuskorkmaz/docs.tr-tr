---
title: Örnek Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1cfaa0db5b81858b733343f17cae71e5815ef60b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596638"
---
# <a name="instancing"></a>Örnek Oluşturma
Örnek oluşturma örneği, bir hizmet sınıfı örneklerinin istemci isteklerine yanıt olarak nasıl oluşturulduğunu denetleyen örnek oluşturma davranış ayarını gösterir. Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` . Bu örnek, öğesinden devralan yeni bir sözleşme tanımlar `ICalculatorInstance` `ICalculator` . Tarafından belirtilen sözleşme, `ICalculatorInstance` hizmet örneğinin durumunu incelemek için üç ek işlem sağlar. Örnek ayarını değiştirerek, istemcisini çalıştırarak değişiklik davranışını gözlemleyebilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Aşağıdaki örnek oluşturma modları kullanılabilir:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Her istemci isteği için yeni bir hizmet örneği oluşturulur.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Her yeni istemci oturumu için yeni bir örnek oluşturulur ve bu oturumun kullanım ömrü boyunca korunur (oturumu destekleyen bir bağlama gerekir).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Hizmet sınıfının tek bir örneği, uygulamanın kullanım ömrü boyunca tüm istemci isteklerini işler.  
  
 Service sınıfı, `[ServiceBehavior(InstanceContextMode=<setting>)]` Aşağıdaki kod örneğinde gösterildiği gibi özniteliği ile örnek oluşturma davranışını belirtir. Hangi satırların açıklama olarak değiştirildiğini değiştirerek, her örnek modunun davranışını gözlemleyebilirsiniz. Örnek oluşturma modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın. İstemcide belirtmek için örnek oluşturma ile ilgili ayarlar yoktur.  
  
```csharp
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Hizmetin altında çalıştığı örnek modu görüntülenir. Her işlemden sonra örnek KIMLIĞI ve işlem sayısı, örnek oluşturma modunun davranışını yansıtacak şekilde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
