---
title: Varsayılan Hizmet Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 31c6e0b8bf2b058fbefa76f48ade39ba8e7def69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961763"
---
# <a name="default-service-behavior"></a>Varsayılan Hizmet Davranışı
Bu örnek, hizmet davranışı ayarlarının nasıl yapılandırılacağını gösterir. Örnek, `ICalculator` hizmet sözleşmesini uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır. Bu örnek, <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini kullanarak hizmet davranışlarını ve işlem davranışlarını açıkça tanımlar. Yapılandırma dosyalarındaki veya koddaki imperatively (Bu örnekte gösterildiği gibi) davranışları yapılandırabilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet sınıfı, aşağıdaki kod örneğinde gösterildiği <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> gibi, ve içeren davranışları belirtir. Belirtilen tüm değerler varsayılan değerlerdir.  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 Hizmet davranışları <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğiyle belirtilir. Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.  
  
|Hizmet davranışı|Açıklama|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|İstemci isteğindeki bir oturumu otomatik olarak kapatır.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Her hizmet örneği için eşzamanlılık modunu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Örnek bağlam modunu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Bir ayarlanmışsa, belirtilen eşitleme bağlamının kullanılıp kullanılmayacağını belirler. Windows Forms uygulamalarında kullanmak `WindowsFormsSynchronizationContext` isteyip istemediğinizi denetlemek istediğinizde bunu kullanın.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Genel işlenmemiş yürütme özel durumlarının bir `Fault<string>` hata iletisi olarak dönüştürülüp dönüştürülmeyeceğini ve gönderilip gönderilmeyeceğini belirler.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|İşlemler için yalıtım düzeyini belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Beklenmeyen ileti üstbilgilerinin hata koşuluna neden olup olmadığını belirler.|  
  
 İşlem davranışları <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği kullanılarak belirtilir. Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.  
  
|İşlem davranışı|Açıklama|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Hizmet işleminin tamamlanmasının geçerli işlemi yürütmeyeceğini belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Hizmet işleminin istemci tarafından akışlı bir işlemde görüntülenip görüntülenmeyeceğini belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Hizmet işleminin arayanın kimliğini taklit etmediğini belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Hizmet örneklerinin, hizmet işlemi çağrısının başlangıcında veya sonunda geri dönüştürülüp dönüştürülmeyeceğini belirler.|  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Çağrılar arasındaki gecikme, hizmet işlemlerinde `System.Threading.Thread.Sleep()` yapılan çağrıların sonucudur. Davranış örneklerinin geri kalanı bu davranışları daha ayrıntılı bir şekilde açıklamaktadır. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
