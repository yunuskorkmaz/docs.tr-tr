---
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 6a0a1c5d9f9741da978c633d35ea1e39664bed5b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716300"
---
# <a name="service-debug-behavior"></a>Hizmet Hata Ayıklama Davranışı

Bu örnek, hizmet hata ayıklama davranışı ayarlarının nasıl yapılandırılacağını gösterir. Örnek, `ICalculator` hizmet sözleşmesini uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Bu örnek, yapılandırma dosyasında hizmet hata ayıklama davranışını açıkça tanımlar. Ayrıca, kod içinde imperatively de yapılabilir.

Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Sunucu için Web. config dosyası, aşağıdaki örnekte gösterildiği gibi yardım sayfası ve özel durum işlemeyi etkinleştirmek için hizmet hata ayıklama davranışını tanımlar.

```xml
<behaviors>
     <serviceBehaviors>
         <behavior name="CalculatorServiceBehavior">
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->
         <!-- Please set this to false when deploying -->
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>
         </behavior>
     </serviceBehaviors>
</behaviors>
```

[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) , hizmet hata ayıklama davranışı özelliklerinin değiştirilmesini sağlayan yapılandırma öğesidir. Kullanıcı bu davranışı değiştirerek aşağıdakileri elde edebilir:

- Bu, özel durum <xref:System.ServiceModel.FaultContractAttribute>kullanılarak bildirilmemiş olsa bile, hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar. `includeExceptionDetailInFaults` `true`olarak ayarlanarak yapılır. Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır.

  > [!IMPORTANT]
  > Bu ayarı bir üretim ortamında açmak güvenli değildir. Beklenmeyen bir sunucu özel durumu, istemciye yönelik amaçlı olmayan bazı bilgiler içerebilir ve `includeExceptionDetailsInFaults` `true` ayarı bir bilgi sızıntısına neden olabilir.

- [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) , kullanıcının yardım sayfasını etkinleştirmesine veya devre dışı bırakmasına izin verir. Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir. Bu, `httpHelpPageEnabled` `true`ayarlanarak etkinleştirilebilir. Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar. Başka bir öznitelik `httpHelpPageUrl`ayarlayarak bu adresi değiştirebilirsiniz. Bunu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz. Bu, `httpsHelpPageEnabled` ve `httpsHelpPageUrl`ayarlanarak yapılabilir.

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İlk üç işlem (ekleme, çıkarma ve çarpma) başarılı olmalıdır. Son işlem ("Böl"), sıfıra bölme özel durumuyla başarısız olur.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
