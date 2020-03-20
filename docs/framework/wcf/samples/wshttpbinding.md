---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143375"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Bu örnek, Windows Communication Foundation (WCF) kullanan tipik bir hizmetin ve tipik bir istemcinin nasıl uygulanacağını gösterir. Bu örnek, bir istemci konsol programı (client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini `ICalculator` (ekleme, çıkarma, çoğaltma ve bölme) ortaya çıkaran arabirim tarafından tanımlanır. İstemci belirli bir matematik işlemi için eşzamanlı isteklerde bulunmaz ve sonuç ile hizmet yanıtları. İstemci etkinliği konsol penceresinde görünür.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek `ICalculator` [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanarak sözleşme ortaya çıkarır. Bu bağlamayapılandırması Web.config dosyasında genişletildi.  
  
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
  
 Temel `binding` öğede, `maxReceivedMessageSize` değer gelen iletinin (baytiçinde) en büyük boyutunu yapılandırmanızı sağlar. Değer, `hostNameComparisonMode` hizmete iletileri de-multiplexing zaman ana bilgisayar adı kabul edilip olmadığını yapılandırmanızı sağlar. Değer, `messageEncoding` iletiler için Metin veya MTOM kodlaması kullanıp kullanmayacağını yapılandırmanızı sağlar. Değer, `textEncoding` iletiler için karakter kodlamasını yapılandırmanızı sağlar. Değer, `bypassProxyOnLocal` yerel iletişim için bir HTTP proxy'si kullanıp kullanmayacağını yapılandırmanızı sağlar. Değer, `transactionFlow` geçerli hareketin akışlanıp akışılmayacağını (bir işlem işlem akışı için yapılandırılırsa) yapılandırır.  
  
 Güvenilir Oturum>öğesinde, etkin Boolean değeri güvenilir oturumların etkin olup olmadığını yapılandırır. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) Değer, `ordered` ileti siparişinin korunup korunmadığını yapılandırır. Değer, `inactivityTimeout` bir oturumun hata yapmadan önce ne kadar süre boşta bırakılabildiğini yapılandırır.  
  
 Güvenlik>, `mode` değer hangi güvenlik modunun kullanılması gerektiğini yapılandırır. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) Bu örnekte, iletigüvenliği kullanılıyor, bu nedenle [ \<ileti>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ \<güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)içinde belirtilir.  
  
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
