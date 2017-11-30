---
title: "WS Güvenilir Oturum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec04c91237516bcf535963c2d5ff7b0584c52be2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ws-reliable-session"></a>WS Güvenilir Oturum
Bu örnek güvenilir oturumlar kullanımını göstermektedir. Güvenilir oturumlar güvenilir Mesajlaşma ve oturumlar için destek sağlar. Güvenilir Mesajlaşma iletişim başarısızlığı yeniden deneme ve teslim Güvenceleri gibi iletilerin sıralı varış belirtilmesine izin verir. Oturum durumu çağrıları arasında istemcileri için korur. Örnek istemci durumunu korumak için oturumları uygular ve sıralı teslim Güvenceleri belirtir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular. Güvenilir oturum özellikleri etkinleştirilmiş ve uygulama yapılandırma dosyaları istemci ve hizmet için yapılandırılır.  
  
 Bu örnekte, Internet Information Services (IIS) barındırılan hizmetindeki ve istemcinin bir konsol uygulaması (.exe).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örnek kullanır `wsHttpBinding`. Bağlama, hem istemci hem de hizmet yapılandırma dosyalarında belirtilir. Uç nokta öğesinin belirtilen bağlama türü `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Uç nokta içeren bir `bindingConfiguration` adlı bir bağlama yapılandırması başvuran öznitelik "Binding1." Güvenilir oturumlar ayarlayarak bağlama yapılandırması sağlar `enabled` özniteliği [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) için `true`. Sıralı oturumları için teslim Güvenceleri sıralı özniteliğini tarafından denetlenen `true` veya `false`. Varsayılan, `true` değeridir.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Hizmet uygulaması sınıfı uygulayan <xref:System.ServiceModel.InstanceContextMode.PerSession> örneklemesini aşağıdaki örnek kodda gösterildiği gibi her bir istemci için ayrı sınıf örneğinin korumak için.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
