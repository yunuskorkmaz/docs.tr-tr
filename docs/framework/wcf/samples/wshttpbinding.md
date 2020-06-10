---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: a78eac52095d3f647efdacc9104a75e46651f389
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596377"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Bu örnek, Windows Communication Foundation (WCF) kullanılarak tipik bir hizmetin ve tipik bir istemcinin nasıl uygulanacağını gösterir. Bu örnek, bir istemci konsol programından (Client. exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, `ICalculator` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır. İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir. İstemci etkinliği konsol penceresinde görünür.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek `ICalculator` , kullanarak sözleşmeyi kullanıma sunar [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . Bu bağlamanın yapılandırması Web. config dosyasında genişletildi.  
  
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
  
 Taban `binding` öğesinde `maxReceivedMessageSize` değeri, gelen bir iletinin en büyük boyutunu (bayt cinsinden) yapılandırmanıza olanak tanır. `hostNameComparisonMode`Değer, ana bilgisayar adının hizmete ileti serbest bırakıldığında kabul edilip edilmeyeceğini yapılandırmanızı sağlar. `messageEncoding`Değer, iletiler Için metin veya MTOM kodlamasının kullanılıp kullanılmayacağını yapılandırmanızı sağlar. `textEncoding`Değer, iletiler için karakter kodlamasını yapılandırmanızı sağlar. `bypassProxyOnLocal`Değer, yerel iletişim için BIR http proxy 'si kullanıp kullanmayacağınızı yapılandırmanıza olanak tanır. `transactionFlow`Değer, geçerli işlemin akan olup olmadığını yapılandırır (işlem akışı için bir işlem yapılandırılmışsa).  
  
 [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md)Öğesinde, etkin Boole değeri, güvenilir oturumların etkinleştirilip etkinleştirilmeyeceğini yapılandırır. `ordered`Değer, ileti sıralamasını korunup korunmadığını yapılandırır. `inactivityTimeout`Değer, bir oturumun hata vermeden önce ne kadar süreyle boşta kalabileceğini yapılandırır.  
  
 Üzerinde, [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` değeri hangi güvenlik modunun kullanılması gerektiğini yapılandırır. Bu örnekte, ileti güvenliği kullanılmaktadır, bu neden [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) içinde belirtilir [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) .  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
