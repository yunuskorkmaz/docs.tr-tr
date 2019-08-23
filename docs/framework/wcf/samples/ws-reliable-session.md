---
title: WS Güvenilir Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 604eaf9dc2ef506214969826ee7f38ee85690a0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942181"
---
# <a name="ws-reliable-session"></a>WS Güvenilir Oturum
Bu örnek, güvenilir oturumların kullanımını gösterir. Güvenilir Oturumlar, güvenilir mesajlaşma ve oturumlar için destek sağlar. Güvenilir Mesajlaşma, hata durumunda iletişim kurmayı yeniden dener ve mesajların, iletilerin sıralı gelişmesi gibi belirli bir şekilde belirtilmesini sağlar. Oturumlar, çağrılar arasındaki istemciler için durumu korur. Örnek, istemci durumunun sürdürülmesi için oturumları uygular ve sıralı teslim bildirimlerini belirtir.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır. Güvenilir oturum özellikleri, istemci ve hizmet için uygulama yapılandırma dosyalarında etkinleştirilir ve yapılandırılır.  
  
 Bu örnekte, hizmet Internet Information Services (IIS) içinde barındırılır ve istemci bir konsol uygulaması (. exe).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnek öğesini kullanır `wsHttpBinding`. Bağlama, hem istemci hem de hizmet için yapılandırma dosyalarında belirtilir. Bağlama türü, aşağıdaki örnek yapılandırmada gösterildiği gibi Endpoint öğesinin `binding` özniteliğinde belirtilir.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Uç nokta, " `bindingConfiguration` Binding1" adlı bağlama yapılandırmasına başvuran bir öznitelik içeriyor. Bağlama yapılandırması, `enabled` [ \<reliableoturum >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) özniteliğini olarak `true`ayarlayarak güvenilir oturumlara olanak sağlar. Sıralı oturumlar için teslim kesintileri, sıralanmış özniteliği veya `true` `false`olarak ayarlanarak denetlenir. Varsayılan, `true` değeridir.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Hizmet uygulama sınıfı, aşağıdaki <xref:System.ServiceModel.InstanceContextMode.PerSession> örnek kodda gösterildiği gibi her istemci için ayrı bir sınıf örneği tutmak üzere örnek oluşturma uygular.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
