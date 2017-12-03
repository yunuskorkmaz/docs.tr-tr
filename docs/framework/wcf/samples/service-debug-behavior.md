---
title: "Hizmet Hata Ayıklama Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb609857dbe3aaee0014e284d80af3b93ac395e5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="service-debug-behavior"></a>Hizmet Hata Ayıklama Davranışı
Bu örnek, hizmet hata ayıklama davranışı ayarları nasıl yapılandırılabilir gösterir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme. Bu örnek, hizmet hata ayıklama davranışı yapılandırma dosyasında açıkça tanımlar. Bu da imperatively kodda yapılabilir.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Sunucu için Web.config dosyasının Yardım sayfası ve aşağıdaki örnekte gösterildiği gibi özel durum işleme etkinleştirmek için hizmet hata ayıklama davranışı tanımlar.  
  
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
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) hizmet hata ayıklama davranışı özelliklerini değiştirme sağlayan yapılandırma öğesidir. Kullanıcı aşağıdakileri gerçekleştirmek için bu davranışı değiştirebilirsiniz:  
  
-   Özel durum kullanarak bildirilmedi olsa bile uygulama kodu tarafından oluşturulan özel durumları döndürülecek hizmetin böylece <xref:System.ServiceModel.FaultContractAttribute>. Ayarlayarak yapılır `includeExceptionDetailInFaults` için `true`. Bu ayar, sunucu beklenmeyen bir özel durum burada atma durumlarda hata ayıklama sırasında yararlıdır.  
  
    > [!IMPORTANT]
    >  Bir üretim ortamında bu ayarı etkinleştirmek için güvenli değildir. Beklenmeyen sunucu özel durum istemci ve bunu ayarı amaçlanmamıştır bazı bilgiler olabilir `includeExceptionDetailsInFaults` için `true` içinde bilgi sızıntısı neden olabilir.  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) Ayrıca, kullanıcının etkinleştirme veya devre dışı yardım sayfasına izin verir. Her hizmet, isteğe bağlı olarak hizmet için WSDL almak için uç nokta da dahil olmak üzere hizmeti hakkında bilgi içeren bir Yardım sayfası getirebilir. Bu ayarlayarak etkinleştirilebilir `httpHelpPageEnabled` için `true`. Bu hizmetin taban adresi için bir GET isteğine döndürülecek Yardım sayfası sağlar. Başka bir öznitelik ayarlayarak bu adresi değiştirebilirsiniz `httpHelpPageUrl`. Bu HTTP yerine HTTPS kullanılarak güvenli hale getirebilir. Bu ayar yapılabilir `httpsHelpPageEnabled` ve `httpsHelpPageUrl`.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İlk üç işlemleri (eklemek, çıkarmak ve çarpma) başarılı olması gerekir. Son işlem ("bölme") ile bölme sıfır bir özel durum nedeniyle başarısız olur.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>Ayrıca Bkz.
