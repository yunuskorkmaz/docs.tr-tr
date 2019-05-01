---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: d8453d85afb92c69bdf3066ccb8b31e26a34c6d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006492"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Bu örnek, tipik bir hizmet ve Windows Communication Foundation (WCF) kullanan tipik bir istemciye uygulamak nasıl gösterir. Bu örnek, bir istemci konsol programı'nı (client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı oluşur. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme). İstemci verilen matematik işlemi ve hizmet yanıt sonucu zaman uyumlu istekleri yapar. İstemci etkinliği konsol penceresinde görünür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek gösterir `ICalculator` kullanarak sözleşme [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Bu bağlama yapılandırmasını Web.config dosyasında genişletildi.  
  
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
  
 Taban `binding` öğesi `maxReceivedMessageSize` değeri en büyük boyutunu (bayt cinsinden) gelen ileti yapılandırmanıza olanak sağlar. `hostNameComparisonMode` Değeri ana bilgisayar hizmete XML'deki çoğullama, iletileri kabul olmadığını yapılandırmanızı sağlar. `messageEncoding` Değeri iletiler için metin veya MTOM kodlama kullanıp kullanmayacağınızı yapılandırmanıza olanak sağlar. `textEncoding` Değeri karakter kodlaması için iletileri yapılandırmanıza olanak sağlar. `bypassProxyOnLocal` Değer yerel iletişim için bir HTTP proxy kullanıp kullanmayacağınızı yapılandırmanıza olanak sağlar. `transactionFlow` Değeri, geçerli işlem (bir işlem için işlem akışı yapılandırılmışsa) akıtılan olup olmadığını yapılandırır.  
  
 Üzerinde [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) öğesi, etkin bir Boole değeri yapılandırır güvenilir oturumlar etkinleştirilip etkinleştirilmediğini. `ordered` Değer ileti sıralama korundu olup olmadığını yapılandırır. `inactivityTimeout` Değer ne kadar bir oturumun hatalı önce boşta kalabileceği yapılandırır.  
  
 Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır. Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
