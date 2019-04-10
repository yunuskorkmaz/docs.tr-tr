---
title: Varsayılan Hizmet Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 5bfaab536bdc4725a22f8451b18c000649ce8aeb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226605"
---
# <a name="default-service-behavior"></a>Varsayılan Hizmet Davranışı
Bu örnek, hizmet davranışı ayarları nasıl yapılandırılabileceğini göstermektedir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi. Bu örnek hizmet davranışları ve işlem davranışları kullanarak açıkça tanımlar <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikleri. (Bu örnekte gösterildiği gibi), yapılandırma dosyalarında veya kesin kod davranışlarını yapılandırabilirsiniz.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmet sınıfını içeren davranışlar belirtir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> aşağıdaki kod örneğinde gösterildiği gibi. Belirtilen tüm varsayılan değerler.  
  
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
  
 Hizmet davranışları ile belirtilen <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği. Aşağıdaki tabloda bu davranışların bazılarını açıklar.  
  
|Hizmet davranışı|Açıklama|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Otomatik olarak istemci isteğinde bir oturumu kapatır.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Her hizmet örneği için eşzamanlılık modunu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Örnek içerik modu belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Biri ayarlanmışsa belirtilen eşitleme bağlamı kullanılıp kullanılmayacağını belirler. Kullanılıp kullanılmayacağını kontrol etmek istediğinizde bunu kullanmak bir `WindowsFormsSynchronizationContext` Windows Forms uygulamalarındaki.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Genel işlenmemiş yürütme özel durumları dönüştürülecek olup olmadığını belirler bir `Fault<string>` ve bir hata iletisi gönderilir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|İşlem yalıtım düzeyini belirtir.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Beklenmeyen ileti üstbilgileri hata durumuna neden olup olmadığını belirler.|  
  
 İşlem davranışları kullanarak belirtilen <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği. Aşağıdaki tabloda bu davranışların bazılarını açıklar.  
  
|İşlem davranışı|Açıklama|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Hizmet işlemi tamamlama geçerli işlem yürütmeleri olup olmadığını belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Hizmet işlemi istemci akışı yapılan işlemler bir işlemde kaydeder olup olmadığını belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Hizmet işlemi çağıranın kimliğini taklit olup olmadığını belirler.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Hizmet örnekleri başlangıç veya bitiş hizmet işlemi çağrısının geri olup olmadığını belirler.|  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Çağrılar arasındaki gecikmeyi çağrıları sonucudur `System.Threading.Thread.Sleep()` hizmet işlemlerinde yapılan. Davranış örnekleri geri kalanını Bu davranışların daha ayrıntılı açıklanmaktadır. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
