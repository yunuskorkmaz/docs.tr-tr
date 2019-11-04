---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 5a2d190fe7dfd5305b47da0e6e67de822cfd695b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424453"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Bu örnek, Windows Communication Foundation (WCF) kullanılarak tipik bir hizmetin ve tipik bir istemcinin nasıl uygulanacağını gösterir. Bu örnek, bir istemci konsol programından (Client. exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculator` arabirimi tarafından tanımlanır. İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir. İstemci etkinliği konsol penceresinde görünür.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, `ICalculator` sözleşmesini [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanarak gösterir. Bu bağlamanın yapılandırması Web. config dosyasında genişletildi.  
  
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
  
 Temel `binding` öğesinde, `maxReceivedMessageSize` değeri gelen iletinin en büyük boyutunu (bayt cinsinden) yapılandırmanıza olanak tanır. `hostNameComparisonMode` değeri, ana bilgisayar adının hizmete ileti serbest bırakıldığında kabul edilip edilmeyeceğini yapılandırmanızı sağlar. `messageEncoding` değeri, iletiler için metin veya MTOM kodlamasının kullanılıp kullanılmayacağını yapılandırmanızı sağlar. `textEncoding` değeri iletiler için karakter kodlamasını yapılandırmanıza olanak tanır. `bypassProxyOnLocal` değeri, yerel iletişim için bir HTTP proxy 'si kullanıp kullanmayacağınızı yapılandırmanıza olanak tanır. `transactionFlow` değeri, geçerli işlemin akan olup olmadığını yapılandırır (işlem akışı için bir işlem yapılandırılmışsa).  
  
 [\<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) öğesinde, etkin Boole değeri, güvenilir oturumların etkinleştirilip etkinleştirilmeyeceğini yapılandırır. `ordered` değeri, ileti sıralamasını korunup korunmadığını yapılandırır. `inactivityTimeout` değeri, bir oturumun hata vermeden önce ne kadar süreyle boşta kalabileceğini yapılandırır.  
  
 [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)`mode` değeri hangi güvenlik modunun kullanılması gerektiğini yapılandırır. Bu örnekte ileti güvenliği, [\<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) neden [\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)içinde belirtilmekte kullanılır.  
  
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
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
