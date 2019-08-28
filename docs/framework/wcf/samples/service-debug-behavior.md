---
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 67ae8cf72baf2d6a54010a05ca4c5e047120617a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044739"
---
# <a name="service-debug-behavior"></a>Hizmet Hata Ayıklama Davranışı

Bu örnek, hizmet hata ayıklama davranışı ayarlarının nasıl yapılandırılacağını gösterir. Örnek, `ICalculator` hizmet sözleşmesini uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır. Bu örnek, yapılandırma dosyasında hizmet hata ayıklama davranışını açıkça tanımlar. Ayrıca, kod içinde imperatively de yapılabilir.

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

serviceDebug >, hizmet hata ayıklama davranışı özelliklerinin değiştirilmesini sağlayan yapılandırma öğesidir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) Kullanıcı bu davranışı değiştirerek aşağıdakileri elde edebilir:

- Bu, özel durum kullanılarak <xref:System.ServiceModel.FaultContractAttribute>bildirilmemiş olsa bile hizmetin uygulama kodu tarafından oluşturulan herhangi bir özel durumu döndürmesini sağlar. `includeExceptionDetailInFaults` Ayarıyla`true`yapılır. Bu ayar, sunucunun beklenmeyen bir özel durum oluşturan durumlarda hata ayıklaması yaparken faydalıdır.

  > [!IMPORTANT]
  > Bu ayarı bir üretim ortamında açmak güvenli değildir. Beklenmeyen bir sunucu özel durumu, istemciye yönelik amaçlı olmayan bazı bilgiler içerebilir ve bu nedenle ayarı `includeExceptionDetailsInFaults` `true` bilgi sızıntısına neden olabilir.

- ServiceDebug > Ayrıca bir kullanıcının yardım sayfasını etkinleştirmesine veya devre dışı bırakmasına izin verir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) Her hizmet, isteğe bağlı olarak hizmetle ilgili WSDL 'yi almak için uç nokta dahil olmak üzere hizmet hakkındaki bilgileri içeren bir yardım sayfası sunabilir. Bu, ayarına `httpHelpPageEnabled` `true`göre etkinleştirilebilir. Bu, yardım sayfasının, hizmetin temel adresine yönelik bir GET isteğine döndürülmesini sağlar. Başka bir öznitelik `httpHelpPageUrl`ayarlayarak bu adresi değiştirebilirsiniz. Bunu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz. Bu, ve `httpsHelpPageEnabled` `httpsHelpPageUrl`ayarı ile yapılabilir.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
