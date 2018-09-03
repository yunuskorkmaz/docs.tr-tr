---
title: Windows Hizmet Uygulamasında Barındırma
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: 2b3935babec0c7cdc3ffca5dd11d693fdfee7a89
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483102"
---
# <a name="hosting-in-a-windows-service-application"></a>Windows Hizmet Uygulamasında Barındırma
(Eski adıyla Windows NT Hizmetleri da bilinir) Windows hizmetleri sağlayan bir işlem modeli özellikle uzun süre çalışan bir yürütülebilir dosya bulunmalıdır ve herhangi bir biçimde kullanıcı arabirimi gösterme uygulamalar için uygundur. Hizmet uygulaması başlatmaya olanak tanıyan hizmet denetimi yöneticisi tarafından (SCM), yönetilen bir Windows işlem ömrü durdurun ve Windows hizmeti uygulamalarını duraklatma. "Always on" uygulamalar için uygun bir barındırma ortamı yapmadan bilgisayar başlatıldığında otomatik olarak başlayacak şekilde bir Windows hizmeti işlemi yapılandırabilirsiniz. Windows hizmeti uygulamaları hakkında daha fazla bilgi için bkz: [Windows hizmet uygulamaları](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Uzun süre çalışan Windows Communication Foundation (WCF) hizmetlerini barındıran uygulamalar, Windows Hizmetleri ile birçok ortak özelliklere sahiptir. Özellikle, WCF hizmetleri doğrudan kullanıcı ile etkileşimde bulunmazlar ve herhangi bir biçimde kullanıcı arabirimini uygulamayan uzun süre çalışan sunucu yürütülebilir dosyaları oluşturulur. Bu nedenle, bir Windows hizmeti uygulaması içinde WCF hizmetlerini barındıran sağlam, uzun süre çalışan, WCF uygulamaları oluşturmaya yönelik bir seçenektir.  
  
 Genellikle, WCF geliştiricileri içinde bir Windows hizmeti uygulaması veya Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırma ortamı içinde WCF uygulamalarını barındırmak karar vermeniz gerekir. Windows hizmet uygulamaları aşağıdaki koşullarda kullanmayı düşünmeniz gerekir:  
  
-   Uygulamanızı açık etkinleştirme gerektirir. Örneğin, dinamik olarak ilk gelen iletiye yanıt olarak Başlatılmakta olan yerine sunucu başlatıldığında yapılacak uygulamanızı otomatik olarak başlamalıdır, Windows Hizmetleri kullanmanız gerekir.  
  
-   Uygulamanızı barındıran işlem başlatıldığında çalışır durumda kalması gerekir. Başladıktan sonra bir Windows hizmeti işlemi sürece çalışmaya devam açıkça kapatma hizmeti Denetim Yöneticisi'ni kullanarak yöneticiler tarafından. IIS ya da WAS içinde barındırılan uygulamaları kullanmaya ve sistem kaynakları en iyi kullanılmasını sağlamak için dinamik olarak durduruldu. Kendi barındırma işlemi ömrü boyunca açık denetim gerektiren uygulamalar, IIS veya WAS yerine Windows Hizmetleri kullanmanız gerekir.  
  
-   WCF hizmetinizi, Windows Server 2003'te çalıştırmak ve dışındaki HTTP taşımaları kullanmanız gerekir. Windows Server 2003'te [!INCLUDE[iis601](../../../../includes/iis601-md.md)] barındırma ortamı yalnızca HTTP iletişimi için Yasak. Windows hizmet uygulamaları, bu kısıtlama tabi olmayan ve net.tcp net.pipe ve net.msmq dahil olmak üzere tüm aktarım WCF destekler kullanabilirsiniz.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>İçinde bir Windows hizmeti uygulaması WCF barındırmak için  
  
1.  Bir Windows hizmet uygulaması oluşturun. Windows hizmet uygulamaları sınıfları kullanarak yönetilen kod yazabileceğiniz <xref:System.ServiceProcess> ad alanı. Bu uygulama öğesinden devralınan bir sınıf içermelidir <xref:System.ServiceProcess.ServiceBase>.  
  
2.  WCF hizmetleri ömrünü Windows hizmet uygulaması ömrünü bağlayın. Genellikle, barındırma hizmeti başlatıldığında etkinleşir, barındırma hizmeti durduruldu ve barındırma işlemi WCF hizmeti bir hatayla karşılaştığında Kapat iletileri için dinleyecek şekilde bir Windows hizmet uygulamasında barındırılan WCF hizmetleri için istediğiniz. Bu şekilde gerçekleştirilebilir:  
  
    -   Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> bir veya daha fazla örneğini açmayı <xref:System.ServiceModel.ServiceHost>. Tek bir Windows hizmet uygulaması, bir grup olarak başlatıp birden çok WCF hizmetlerini barındırabilirler.  
  
    -   Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStop%2A> çağrılacak <xref:System.ServiceModel.Channels.CommunicationObject.Closed> üzerinde <xref:System.ServiceModel.ServiceHost> sırasında başlatılan çalışan tüm WCF hizmetleri <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Abone <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> olayı <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceProcess.ServiceController> hata durumunda Windows hizmet uygulamasını kapatmak için sınıf.  
  
     WCF hizmetleri barındıran Windows hizmeti uygulamaları dağıtılır ve haline getirmez Windows hizmet uygulamaları WCF kullanmak gibi aynı şekilde yönetilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceProcess>  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](https://go.microsoft.com/fwlink/?LinkId=94875)  
 [Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Windows Hizmet Konağı](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Hizmet Uygulaması Programlama Mimarisi](https://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
