---
title: Özel Bağlama Güvenilir Oturum
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 76c701aaae368171bc7047784e1dc126937c84f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463934"
---
# <a name="custom-binding-reliable-session"></a>Özel Bağlama Güvenilir Oturum

Özel bir bağlama, ayrık bağlama öğelerinin sıralı bir listesi yle tanımlanır. Bu örnek, özellikle güvenilir oturumları etkinleştirerek, çeşitli aktarım ve ileti kodlama öğeleri ile özel bir bağlama yapılandırmak için nasıl gösterir.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a>Örnek Ayrıntılar

Güvenilir oturumlar, güvenilir mesajlaşma ve oturumlar için özellikler sağlar. Güvenilir mesajlaşma, iletişimi arızaya göre yeniden dener ve iletilerin sırayla gelişi gibi teslimat güvencelerinin belirtilmesini sağlar. Oturumlar, istemciler için aramalar arasındaki durumu korur. Örnek, istemci durumunu korumak için oturumlar uygular ve sipariş içi teslimat güvencelerini belirtir. Örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. Güvenilir oturum özellikleri etkinleştirilir ve istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır.

> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.

Bağlama öğelerinin sıralanması, özel bir bağlama tanımlamada önemlidir, çünkü her biri kanal yığınındaki bir katmanı temsil eder (bkz. [Özel Bağlamalar).](../../../../docs/framework/wcf/extending/custom-bindings.md)

Örnek için hizmet yapılandırması aşağıdaki kod örneğinde gösterildiği gibi tanımlanır.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

Makineler arası bir senaryoda çalışırken, istemcinin uç nokta adresini hizmetin ana bilgisayar adını yansıtacak şekilde değiştirmeniz gerekir.

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4.0 yükleyin:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.

    > [!IMPORTANT]
    > İstemciyi bir çapraz makine yapılandırmasında çalıştırırken, aşağıdaki örnekte `address` gösterildiği gibi, [ \<hem bitiş noktası>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesiözünün `clientBaseAddress` hem de [ \<kompozitDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) özniteliğini aşağıdaki örnekte gösterildiği gibi uygun makinenin adı ile "localhost" olarak değiştirdiğinden emin olun.

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
