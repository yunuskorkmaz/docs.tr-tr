---
title: WS Taşıma Güvenliği
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: d0f357ddcfc355bac8eeb86d57641add0013a052
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596403"
---
# <a name="ws-transport-security"></a>WS Taşıma Güvenliği
Bu örnek, bağlamakla SSL Aktarım güvenliği kullanımını gösterir <xref:System.ServiceModel.WSHttpBinding> . Varsayılan olarak, `wsHttpBinding` bağlama http iletişimi sağlar. Aktarım güvenliği için yapılandırıldığında bağlama, HTTPS iletişimini destekler. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır. , `wsHttpBinding` İstemci ve hizmet için uygulama yapılandırma dosyalarında belirtilir ve yapılandırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 Örnekteki program kodu, [Başlarken](getting-started-sample.md) hizmetindekilerle aynıdır. Örneği oluşturmadan önce bir sertifika oluşturmalı ve Web sunucusu Sertifika sihirbazını kullanarak atamanız gerekir. Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, `Transport` istemci için aşağıdaki örnek yapılandırmada gösterildiği gibi güvenlik modunu etkinleştirir.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 Belirtilen adres `https://` düzeni kullanır. Bağlama yapılandırması güvenlik modunu olarak ayarlar `Transport` . Hizmetin Web. config dosyasında aynı güvenlik modu belirtilmelidir.  
  
 Bu örnekte kullanılan sertifika, MakeCert. exe ile oluşturulmuş bir test sertifikasıdır çünkü, tarayıcınızla, gibi bir https: adresine erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc` . Windows Communication Foundation (WCF) istemcisinin bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir. Üretim sertifikaları kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

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
  
3. [Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.  
  
4. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
5. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
