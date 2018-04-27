---
title: WS Taşıma Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
caps.latest.revision: 22
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 4a332394877e33f6ab97b4be77da6c3267d85401
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="ws-transport-security"></a>WS Taşıma Güvenliği
Bu örnek ile taşıma güvenliği SSL kullanımını gösteren <xref:System.ServiceModel.WSHttpBinding> bağlama. Varsayılan olarak, `wsHttpBinding` bağlama HTTP iletişim sağlar. Taşıma güvenliği için yapılandırıldığında, bağlama HTTPS iletişimi destekler. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular. `wsHttpBinding` Belirtilen ve uygulama yapılandırma dosyaları istemci ve hizmet için yapılandırılır.  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 Örnek program kodunda olarak aynıdır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmet. Bir sertifika oluşturun ve oluşturmaya ve örnek çalıştırmaya önce Web Sunucusu Sertifika Sihirbazı'nı kullanarak atamanız gerekir. Uç nokta tanımı ve bağlama tanımı dosyası ayarlarını etkinleştir `Transport` istemci için aşağıdaki örnek yapılandırma gösterildiği gibi güvenlik modu.  
  
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
  
 Belirtilen adres https:// düzenini kullanır. Güvenlik modu bağlama yapılandırması ayarlar `Transport`. Aynı güvenlik modu hizmetin Web.config dosyasında belirtilmesi gerekir.  
  
 Bu örnekte kullanılan sertifikanın Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir https erişmeye çalıştığınızda bir güvenlik uyarısı görünür: gibi adres https://localhost/servicemodelsamples/service.svc, tarayıcınızdan. İzin vermek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci, yerinde bir test sertifikası ile çalışmak için bazı ek kod güvenlik uyarıyı gizlemek için istemciye eklendi. Bu kod, eşlik eden sınıfı değil ve gerekli üretim sertifikalar kullanıldığında.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
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
  
3.  Gerçekleştirmiş emin olun [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
