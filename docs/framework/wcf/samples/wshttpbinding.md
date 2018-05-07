---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: d76ec0292ea6f8143e641b771daeac8975e91b02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wshttpbinding"></a>WSHttpBinding
Bu örnek, tipik bir hizmet ve Windows Communication Foundation (WCF) kullanan tipik bir istemciye uygulamak üzere gösterilmiştir. Bu örnek, bir istemci konsol programı (client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı oluşur. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme). İstemci eş zamanlı istekleri verilen matematik işlemi ve sonuç ile hizmet yanıtları yapar. İstemci etkinliği konsol penceresinde görünür olur.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek sunan `ICalculator` kullanarak sözleşme [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Bu bağlama yapılandırmasını Web.config dosyasında genişletilmiştir.  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 Tabanında `binding` öğesi, `maxReceivedMessageSize` değeri en büyük boyutunu (bayt cinsinden) gelen ileti yapılandırmanıza olanak sağlar. `hostNameComparisonMode` Değer hostname XML'deki çoğullama hizmete zaman iletileri kabul olup olmadığını yapılandırmanızı sağlar. `messageEncoding` Değeri iletileri için metin veya MTOM kodlama kullanılıp kullanılmayacağını yapılandırmanıza olanak sağlar. `textEncoding` Değeri iletileri için karakter kodlamasını yapılandırmanıza olanak sağlar. `bypassProxyOnLocal` Değeri yerel iletişim için bir HTTP proxy kullanıp kullanmayacağınızı yapılandırmanıza olanak sağlar. `transactionFlow` Değeri, geçerli işlem (bir işlem için işlem akışı yapılandırılmışsa) akıtılan olup olmadığını yapılandırır.  
  
 Üzerinde [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) öğesi, etkin Boole değeri yapılandırır güvenilir oturumlar etkinleştirilip etkinleştirilmediğini. `ordered` Değeri ileti sıralama korundu olup olmadığını yapılandırır. `inactivityTimeout` Değer ne kadar bir oturumun hatalı önce boşta kalabileceği yapılandırır.  
  
 Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır. Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
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
