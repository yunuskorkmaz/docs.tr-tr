---
title: WS Güvenilir Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 660fb9a7f60bc95a5039cdf3bad098c330ac969e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682689"
---
# <a name="ws-reliable-session"></a>WS Güvenilir Oturum
Bu örnek, güvenilir oturumlar kullanımını gösterir. Güvenilir oturumlar, güvenilir Mesajlaşma ve oturumlar için destek sağlıyor. Güvenilir Mesajlaşma iletişimi hatasında yeniden deneme sayısı ve teslim Güvenceleri gibi iletilerin sıralı varış belirtilmesini sağlar. Oturumlarının çağrıları arasında istemcilerin zachovat stav relace Örnek oturumları, istemci durum koruma için uygular ve sıralı teslim Güvenceleri belirtir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan. Güvenilir oturum özellikleri etkin ve uygulama yapılandırma dosyalarında istemci ve hizmet için yapılandırılır.  
  
 Bu örnekte, Internet Information Services (IIS) barındırılan hizmetin ve bir konsol uygulaması (.exe) istemcidir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örnek kullanır `wsHttpBinding`. Hem istemci hem de hizmet yapılandırma dosyalarında bağlama belirtildi. Uç nokta öğenin belirtilen bağlama türü `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Uç nokta içeren bir `bindingConfiguration` bağlama yapılandırması başvuran öznitelik adında "Binding1." Bağlama yapılandırması güvenli oturumlar ayarlayarak sağlar `enabled` özniteliği [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) için `true`. Sıralı oturumlar için teslim Güvenceleri sıralı özniteliğini tarafından denetlenen `true` veya `false`. Varsayılan, `true` değeridir.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Hizmet uygulaması sınıf uygulayan <xref:System.ServiceModel.InstanceContextMode.PerSession> örneklemesini aşağıdaki örnek kodda gösterildiği gibi her istemci için ayrı bir sınıf örneğinin korumak için.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
