---
title: Windows Hizmet Uygulamasında Barındırma
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: e440961055ccd40bf56b4b88ea73d167f1903245
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-in-a-windows-service-application"></a>Windows Hizmet Uygulamasında Barındırma
(Daha önce Windows NT Hizmetleri bilinen) Windows hizmetleri sağlayan bir işlem modeli özellikle uzun süre çalışan yürütülebilir dosya içinde bulunmalıdır ve herhangi bir kullanıcı arabirimi biçimi gösterme uygulamalar için uygundur. Hizmet uygulaması başlangıç olanak tanıyan, hizmet denetimi yöneticisi tarafından (SCM), yönetilen bir Windows işlem ömrü durdurun ve Windows hizmeti uygulamalarını duraklatma. Bir Windows hizmet işlemi "her zaman açık" uygulamalar için uygun bir barındırma ortamı kolaylaştırarak bilgisayar başlatıldığında otomatik olarak başlayacak şekilde yapılandırabilirsiniz. Windows hizmet uygulamaları hakkında daha fazla bilgi için bkz: [Windows hizmet uygulamaları](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Uzun süre çalışan Windows Communication Foundation (WCF) hizmetlerini barındıran uygulamalar Windows Hizmetleri ile birçok ortak özelliklere sahiptir. Özellikle, WCF hizmetleri doğrudan kullanıcıyla etkileşim değil ve bu nedenle herhangi bir kullanıcı arabirimi biçimi uygulamak uzun süre çalışan sunucu yürütülebilir dosyalar. Bu nedenle, bir Windows hizmet uygulaması içinde WCF hizmetlerini barındıran güçlü, uzun süreli WCF uygulamaları oluşturmaya yönelik bir seçenektir.  
  
 Genellikle, WCF geliştiricilerin kendi WCF uygulaması Windows hizmeti uygulaması içinde veya Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) bir barındırma ortamı içinde barındırmak karar vermeniz gerekir. Windows hizmet uygulamaları aşağıdaki koşullarda kullanmayı düşünmeniz gerekir:  
  
-   Uygulamanızın açık etkinleştirme gerektirir. Örneğin, dinamik olarak ilk gelen iletisine yanıt olarak başlatılmakta yerine sunucu başlatıldığında yapılacak uygulamanızı otomatik olarak başlamalıdır olduğunda Windows Hizmetleri kullanmanız gerekir.  
  
-   Uygulamanızı barındıran işlemin başlatıldığında çalışan kalmalıdır. Başladıktan sonra bir Windows hizmet işlemi sürece çalışmaya devam açıkça Kapatma Hizmet Denetim Yöneticisi'ni kullanarak bir sunucu yöneticisi tarafından. IIS ya da WAS içinde barındırılan uygulamalar başlatıldı ve sistem kaynakları en iyi kullanılmasını sağlamak için dinamik olarak durduruldu. Kendi barındırma işlemi ömrü üzerinde açık denetim gerektiren uygulamalar, IIS ya da WAS yerine Windows Hizmetleri kullanmanız gerekir.  
  
-   WCF Hizmeti Windows Server 2003'te çalıştırın ve HTTP dışında taşımaları kullanmanız gerekir. Windows Server 2003'te [!INCLUDE[iis601](../../../../includes/iis601-md.md)] barındırma ortamı yalnızca HTTP iletişimi için kısıtlanmış. Windows hizmet uygulamaları bu kısıtlama tabi değildir ve net.tcp, net.pipe ve net.msmq dahil olmak üzere tüm aktarım WCF destekler kullanabilirsiniz.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Windows hizmet uygulaması içinde WCF barındırmak için  
  
1.  Windows hizmet uygulaması oluşturun. Windows hizmet uygulamaları sınıflarda kullanarak yönetilen kod yazabilirsiniz <xref:System.ServiceProcess> ad alanı. Bu uygulama öğesinden devralınan bir sınıf içermelidir <xref:System.ServiceProcess.ServiceBase>.  
  
2.  WCF hizmetleri ömrü Windows hizmet uygulaması için kullanım ömrü bağlayın. Genellikle, Windows hizmet uygulamasında barındırma hizmeti başlatıldığında etkinleşir, barındırma hizmeti durdurulur ve WCF hizmeti bir hatayla karşılaştığında barındırma işlemi kapatmak için iletileri dinleyecek barındırılan WCF hizmetleri istiyor. Bu şekilde gerçekleştirilebilir:  
  
    -   Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> bir veya daha fazla örneğini açmayı <xref:System.ServiceModel.ServiceHost>. Tek bir Windows hizmeti uygulama başlatma ve durdurma grup olarak birden çok WCF hizmetleri barındırabilir.  
  
    -   Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStop%2A> çağırmak için <xref:System.ServiceModel.Channels.CommunicationObject.Closed> üzerinde <xref:System.ServiceModel.ServiceHost> sırasında başlatılan çalışan tüm WCF hizmetleri <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Abone <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> olayı <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceProcess.ServiceController> hata durumunda Windows hizmet uygulaması kapatmak üzere sınıfı.  
  
     WCF hizmetleri barındıran Windows hizmet uygulamaları dağıtılan ve WCF hale Windows hizmet uygulamaları kullandığınız gibi aynı şekilde yönetilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceProcess>  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Windows Hizmet Konağı](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Hizmet Uygulaması Programlama Mimarisi](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
