---
title: Varsayılan Hizmet Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183758"
---
# <a name="default-service-behavior"></a>Varsayılan Hizmet Davranışı
Bu örnek, hizmet davranış ayarlarının nasıl yapılandırılabildiğini gösterir. Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır. Bu örnek, hizmet davranışlarını ve işleyiş <xref:System.ServiceModel.ServiceBehaviorAttribute> davranışlarını ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini kullanarak açıkça tanımlar. Yapılandırma dosyalarındaki veya zorunlu olarak koddaki (bu örnekte gösterildiği gibi) davranışları yapılandırabilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmet sınıfı, aşağıdaki kod örneğinde gösterildiği <xref:System.ServiceModel.ServiceBehaviorAttribute> gibi <xref:System.ServiceModel.OperationBehaviorAttribute> davranışları belirtir. Belirtilen tüm değerler varsayılandeğerlerdir.  
  
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
  
 Hizmet davranışları öznitelik <xref:System.ServiceModel.ServiceBehaviorAttribute> ile belirtilir. Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.  
  
|Hizmet davranışı|Açıklama|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Müşterinin isteği üzerine bir oturumu otomatik olarak kapatır.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Her hizmet örneği için eşzamanlılık modunu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Örnek bağlam modunu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Sağlanan eşitleme bağlamını kullanıp kullanmayacağını, ayarlanmış olup olmadığını belirler. Windows Forms uygulamalarında bir uygulama `WindowsFormsSynchronizationContext` kullanıp kullanmayacağını denetlemek istediğinizde bunu kullanın.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Genel işlenmemiş yürütme özel durumlarının a'ya `Fault<string>` dönüştürülüp hata iletisi olarak gönderilip gönderilmeyeceğini belirler.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Hareketler için yalıtım düzeyini belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Beklenmeyen ileti üstbilgilerinin hata durumuna neden olup olmadığını belirler.|  
  
 İşlem davranışları öznitelik kullanılarak <xref:System.ServiceModel.OperationBehaviorAttribute> belirtilir. Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.  
  
|Operasyon Davranışı|Açıklama|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Hizmet işleminin tamamlanmasının geçerli hareketi gerçekleştirip işlemediğini belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Hizmet işleminin istemci tarafından akan bir harekette kaydolup olmadığını belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Hizmet işleminin arayanın kimliğini taklit edip etmediğini belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Hizmet örneklerinin hizmet işlem çağrısının başında mı yoksa sonunda mı geri dönüştürülür olduğunu belirler.|  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Aramalar arasındaki gecikme, hizmet işlemlerinde `System.Threading.Thread.Sleep()` yapılan aramaların sonucudur. Davranış örneklerinin geri kalanı bu davranışları daha ayrıntılı olarak açıklar. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
