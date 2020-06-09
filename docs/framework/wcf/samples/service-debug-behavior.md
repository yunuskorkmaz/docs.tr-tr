---
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 53f21129860c644d09d1a2eb9cb956aecf8ab0ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596649"
---
# <a name="service-debug-behavior"></a>Hizmet Hata Ayıklama Davranışı

Bu örnek, hizmet hata ayıklama davranışı ayarlarının nasıl yapılandırılacağını gösterir. Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` . Bu örnek, yapılandırma dosyasında hizmet hata ayıklama davranışını açıkça tanımlar. Ayrıca, kod içinde imperatively de yapılabilir.

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

[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md), hizmet hata ayıklama davranışı özelliklerinin değiştirilmesini sağlayan yapılandırma öğesidir. Kullanıcı bu davranışı değiştirerek aşağıdakileri elde edebilir:

- Bu, özel durum kullanılarak bildirilmemiş olsa bile hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar <xref:System.ServiceModel.FaultContractAttribute> . Ayarıyla yapılır `includeExceptionDetailInFaults` `true` . Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır.

  > [!IMPORTANT]
  > Bu ayarı bir üretim ortamında açmak güvenli değildir. Beklenmeyen bir sunucu özel durumu, istemciye yönelik amaçlı olmayan bazı bilgiler içerebilir ve bu nedenle ayarı `includeExceptionDetailsInFaults` `true` bilgi sızıntısına neden olabilir.

- [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)Ayrıca, bir kullanıcının yardım sayfasını etkinleştirmesine veya devre dışı bırakmasına izin verir. Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir. Bu, ayarına göre etkinleştirilebilir `httpHelpPageEnabled` `true` . Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar. Başka bir öznitelik ayarlayarak bu adresi değiştirebilirsiniz `httpHelpPageUrl` . Bunu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz. Bu, ve ayarı ile yapılabilir `httpsHelpPageEnabled` `httpsHelpPageUrl` .

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İlk üç işlem (ekleme, çıkarma ve çarpma) başarılı olmalıdır. Son işlem ("Böl"), sıfıra bölme özel durumuyla başarısız olur.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
