---
title: "Varsayılan Hizmet Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6b693c2030cd5da1aac49b9bb87d2eac3630627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="default-service-behavior"></a>Varsayılan Hizmet Davranışı
Bu örnek, hizmet davranış ayarları nasıl yapılandırılabilir gösterir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme. Hizmet davranışları ve işlem davranışları kullanarak bu örnek açıkça tanımlayan <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikleri. (Bu örnek gösterdiği gibi) yapılandırma dosyalarında veya imperatively kodu davranışları yapılandırabilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmet sınıfı davranışlarla belirtir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> aşağıdaki kod örneğinde gösterildiği gibi. Belirtilen tüm varsayılanları değerlerdir.  
  
```  
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
  
 Hizmet davranışları ile belirtilir <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği. Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.  
  
|Hizmet davranışı|Açıklama|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|İstemcinin isteğini oturumunda otomatik olarak kapatır.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Her hizmet örneği için eşzamanlılık modunu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Örnek bağlamı modu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Ayarlanmış bir sağlanan eşitleme bağlamı kullanılıp kullanılmayacağını belirler. Kullanılıp kullanılmayacağını kontrol etmek istediğinizde bunu kullanın bir `WindowsFormsSynchronizationContext` Windows Forms uygulamalarında.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Genel işlenmemiş yürütme özel durumlar dönüştürülür olup olmadığını belirler bir `Fault<string>` ve bir hata iletisi gönderilir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|İşlemler için yalıtım düzeyini belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Beklenmeyen ileti üstbilgilerini hata durumuna neden olup olmadığını belirler.|  
  
 İşlemi davranışları belirtilen kullanarak <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği. Aşağıdaki tabloda bu davranışların bazıları açıklanmaktadır.  
  
|İşlemi davranışı|Açıklama|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Hizmet işlemi tamamlama geçerli işlem tamamlandıktan olup olmadığını belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Hizmet işlemini istemci aktarılan bir işlemde kaydeder olup olmadığını belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Hizmet işlemini çağıranının kimliğini taklit olup olmadığını belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Hizmet örnekleri başlangıç veya bitiş hizmet işlemi çağrısının geri dönüştürüldüğünde olup olmadığını belirler.|  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Çağrıları arasındaki gecikme çağrıları sonucudur `System.Threading.Thread.Sleep()` hizmet işlemlerinde yapılan. Rest davranışı örnekleri bu davranışların daha ayrıntılı açıklanır. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a>Ayrıca Bkz.
