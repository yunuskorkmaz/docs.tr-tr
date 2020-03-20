---
title: WS Güvenilir Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143505"
---
# <a name="ws-reliable-session"></a>WS Güvenilir Oturum
Bu örnek, güvenilir oturumların kullanımını göstermektedir. Güvenilir oturumlar, güvenilir mesajlaşma ve oturumlar için destek sağlar. Güvenilir ileti, iletişimi başarısızlığa göre yeniden dener ve iletilerin sırayla gelmesi gibi teslimat güvencelerinin belirtilmesini sağlar. Oturumlar, istemciler için aramalar arasındaki durumu korur. Örnek, istemci durumunu korumak için oturumlar uygular ve sipariş içi teslimat güvencelerini belirtir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. Güvenilir oturum özellikleri etkinleştirilir ve istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır.  
  
 Bu örnekte, hizmet Internet Information Services (IIS) barındırılır ve istemci bir konsol uygulamasıdır (.exe).  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnek `wsHttpBinding`kullanır. Bağlama, hem istemci hem de hizmet için yapılandırma dosyalarında belirtilir. Bağlama türü, aşağıdaki örnek yapılandırmada `binding` gösterildiği gibi uç nokta öğesi özniteliği belirtilir.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Uç nokta, `bindingConfiguration` "Binding1" adlı bağlayıcı yapılandırmaya başvuran bir öznitelik içerir. Bağlama `enabled` [ \<yapılandırması, güvenilir Session>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) özniteliğini `true`'ne ayarlayarak güvenilir oturumlar sağlar. Sipariş edilen oturumlar için teslimat güvenceleri, sipariş `true` edilen `false`özniteliği ayarlayarak veya . Varsayılan değer: `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Hizmet uygulama sınıfı, <xref:System.ServiceModel.InstanceContextMode.PerSession> aşağıdaki örnek kodda gösterildiği gibi, her istemci için ayrı bir sınıf örneği korumak için instancing uygular.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
