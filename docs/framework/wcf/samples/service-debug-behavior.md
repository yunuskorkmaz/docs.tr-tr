---
title: Hizmet Hata Ayıklama Davranışı
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: d84f3281beee78f8328011026e4d4653c05ed849
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574904"
---
# <a name="service-debug-behavior"></a>Hizmet Hata Ayıklama Davranışı
Bu örnek, hizmet hata ayıklama davranışı ayarları nasıl yapılandırılabileceğini göstermektedir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi. Bu örnek, hizmet hata ayıklama davranışı yapılandırma dosyasında açıkça tanımlar. Bunu de kesin kod içinde yapılabilir.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Sunucu için Web.config dosyasının yardım sayfasına ve aşağıdaki örnekte gösterildiği gibi özel durum işlemeyi etkinleştirmek için hizmet hata ayıklama davranışı tanımlar.  
  
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
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) hizmet hata ayıklama davranışı özelliklerini değiştirme sağlayan yapılandırma öğesi. Kullanıcı şunları gerçekleştirmek için bu davranışı değiştirebilirsiniz:  
  
-   Böylece, özel durum kullanarak bildirilmedi bile uygulama kodu tarafından oluşturulan tüm özel durum döndürülecek hizmetin <xref:System.ServiceModel.FaultContractAttribute>. Ayarlayarak yapılır `includeExceptionDetailInFaults` için `true`. Bu ayar, sunucu beklenmeyen bir özel durum burada atma durumlarda hata ayıklama sırasında yararlıdır.  
  
    > [!IMPORTANT]
    >  Bir üretim ortamında bu ayarı etkinleştirmek için güvenli değildir. Beklenmeyen sunucu özel durum istemci ve bunu ayarlama hedeflenmemiştir bazı bilgiler olabilir `includeExceptionDetailsInFaults` için `true` içinde bilgi sızıntısı neden olabilir.  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) de etkinleştirmek veya devre dışı yardım sayfasına açmasına olanak sağlar. Her bir hizmet, isteğe bağlı olarak hizmet için WSDL almak için uç nokta gibi hizmet hakkındaki bilgileri içeren bir Yardım sayfası kullanıma sunabilirsiniz. Bu ayarlayarak etkinleştirilebilir `httpHelpPageEnabled` için `true`. Bu hizmetin taban adresi için bir GET isteği için döndürülecek yardım sayfasına sağlar. Başka bir özniteliğini ayarlayarak bu adresi değişebilir `httpHelpPageUrl`. Bu HTTP yerine HTTPS kullanarak güvenli hale getirebilirsiniz. Bu ayarlayarak yapılabilir `httpsHelpPageEnabled` ve `httpsHelpPageUrl`.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İlk üç işlemleri (ekleme, çıkarma ve Çarp) başarılı olması gerekir. Son işlem ("bölme") bir bölme sıfır özel durum ile başarısız olur.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>Ayrıca bkz.
