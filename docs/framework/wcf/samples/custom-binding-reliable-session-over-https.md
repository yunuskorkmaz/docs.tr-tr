---
title: HTTPS Üzerinden Özel Bağlama Güvenli Oturum
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: 051e7f56662a2ca67018ae7dd29189ff50245fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183871"
---
# <a name="custom-binding-reliable-session-over-https"></a>HTTPS Üzerinden Özel Bağlama Güvenli Oturum
Bu örnek, Güvenilir Oturumlar ile SSL taşıma güvenliği kullanımını göstermektedir. Güvenilir Oturumlar, WS-Güvenilir Mesajlaşma protokolünü uygular. Güvenilir Oturumlar üzerinden WS-Security oluşturarak güvenli ve güvenilir bir oturum alabilirsiniz. Ancak bazen, bunun yerine SSL ile HTTP aktarım güvenliğini kullanmayı seçebilirsiniz.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a>Örnek Ayrıntılar  
 SSL, paketlerin kendilerinin güvende olmasını sağlar. Bunun WS-Secure Conversation'ı kullanarak güvenilir oturumu güvence altına almaktan farklı olduğunu unutmayın.  
  
 HTTPS üzerinden güvenilir oturum kullanmak için özel bir bağlama oluşturmanız gerekir. Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. Güvenilir oturum bağlama öğesi ve [ \<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)kullanılarak özel bir bağlama oluşturulur. Aşağıdaki yapılandırma özel bağlama dır.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Örnekteki program kodu, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmetiyle aynıdır. Örneği oluşturmadan ve çalıştırmadan önce Web Sunucusu Sertifika Sihirbazı'nı kullanarak bir sertifika oluşturmanız ve atamanız gerekir. Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, istemci için aşağıdaki örnek yapılandırmada gösterildiği gibi özel bağlama kullanımını sağlar.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Belirtilen adres https:// düzenini kullanır.  
  
 Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızdan bir https adresine https://localhost/servicemodelsamples/service.svcerişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir. Windows Communication Foundation (WCF) istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, istemciye güvenlik uyarısını bastırmak için bazı ek kodlar eklendi. Üretim sertifikaları kullanırken bu kod ve beraberindeki sınıf gerekli değildir.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
3. Internet Information Services [(IIS) Server Certificate Kurulum Yönergesi'ni](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizi belirtin.  
  
4. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
5. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
