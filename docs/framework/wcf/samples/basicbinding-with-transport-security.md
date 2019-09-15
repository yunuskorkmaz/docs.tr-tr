---
title: Taşıma Güvenliği ile BasicBinding
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
ms.openlocfilehash: 5f3afdf4648f9e3f9fbef7c2aad39da4dfc67a2c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990163"
---
# <a name="basicbinding-with-transport-security"></a>Taşıma Güvenliği ile BasicBinding

Bu örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`

## <a name="sample-details"></a>Örnek Ayrıntılar

Varsayılan olarak, temel bağlama HTTP iletişimini destekler. Örnek, temel bağlama için taşıma güvenliğinin nasıl etkinleştirileceğini gösterir. Örneği çalıştırmadan önce, bir sertifika oluşturmanız ve Web sunucusu Sertifika Sihirbazı 'Nı kullanarak atamanız gerekir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Örnekteki program kodu, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmetindekilerle aynıdır. Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi güvenli iletişim sağlamak için değiştirilir.

```xml
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
   </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"/>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```

Bu örnekte kullanılan sertifika, MakeCert. exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızda https://localhost/servicemodelsamples/service.svc bir https: adresine erişmeye çalıştığınızda bir güvenlik uyarısı görünür. Windows Communication Foundation (WCF) istemcisinin bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenir. Gerçek sertifikalar kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.

```csharp
// This code is required only for test certificates such as those
// created by Makecert.exe.
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

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4,0 'yi yükler:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

3. [Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.

4. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

5. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.
