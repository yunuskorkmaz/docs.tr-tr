---
title: Internet Information Services'te Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: e9d0e5a165eb2eabae95da9fd1e744a9bd1c201b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786988"
---
# <a name="hosting-in-internet-information-services"></a>Internet Information Services'te Barındırma
Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir seçenek, içinde bir Internet Information Services (IIS) uygulamasıdır. Bu barındırma modeli tarafından kullanılan bir Modeli'ne benzer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve ASP.NET Web hizmeti (ASMX) Web Hizmetleri.  
  
## <a name="versions-of-iis"></a>IIS sürümleri  
 WCF aşağıdaki işletim sistemlerinde aşağıdaki sürümlerinden birinde IIS üzerinde barındırılabilir:  
  
-   IIS 5.1 [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Bu ortam tasarım ve daha sonra bir sunucu işletim sisteminde gibi dağıtılır, IIS tarafından barındırılan uygulamaların geliştirilmesini için kullanışlıdır [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] geliştirilmiş ölçeklenebilirlik, güvenilirlik ve uygulama yalıtımı sunan bir Gelişmiş işlem modeli sağlar. Bu ortama, yalnızca HTTP iletişimi kullanan WCF hizmetleri Üretim dağıtımı için uygundur.  
  
-   IIS 7.0 [!INCLUDE[wv](../../../../includes/wv-md.md)] ve [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. IIS 7.0 olarak aynı Gelişmiş işlem modeli sağlar [!INCLUDE[iis601](../../../../includes/iis601-md.md)], ancak HTTP dışındaki protokoller üzerinden etkinleştirme ve ağ iletişimine izin vermek için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanır. Bu ortam, WCF (HTTP, net.tcp, net.pipe ve net.msmq dahil) tarafından desteklenen herhangi bir ağ protokolü üzerinden iletişim kuran bir WCF hizmetleri geliştirmek için uygundur. WAS hakkında daha fazla bilgi için bkz: [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) çalışır [!INCLUDE[iisver](../../../../includes/iisver-md.md)] ve barındırma ortamı ve WF NET4 WCF hizmetleri için zengin bir uygulama sağlamak için Windows İşlem Etkinleştirme Hizmeti (WAS). Bu işlem yaşam döngüsü yönetimi, işlem geri dönüştürme, paylaşılan barındırma, hızlı hata koruması, işlem tek bırakma, isteğe bağlı etkinleştirme ve sistem durumu izleme avantajına sahip olur. Ayrıntılı bilgi için bkz. [AppFabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=196494) ve [AppFabric barındırma kavramları](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>IIS barındırma avantajları  
 WCF hizmetlerinde IIS barındırma birçok faydası vardır:  
  
-   IIS barındırılan WCF hizmetleri dağıtılır ve tüm diğer IIS uygulamasının gibi yönetilen türü de dahil olmak üzere [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar ve ASMX.  
  
-   IIS işlem etkinleştirme, sistem durumu yönetimi ve barındırılan uygulamaların güvenilirliğini artırmak için özellikler geri dönüştürme sağlar.  
  
-   Gibi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], WCF hizmetleri barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] yararlanabilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] birden çok uygulamanın bulunduğu geliştirilmiş sunucu yoğunluğu ve ölçeklenebilirlik için ortak bir çalışan işlemindeki paylaşılan barındırma modeli.  
  
-   IIS barındırılan WCF hizmetleri kullanma aynı dinamik derleme modelde [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], geliştirme basitleştirir ve dağıtım, barındırılan hizmetler.  
  
 WCF hizmetlerinde IIS konak karar verirken unutmamak gerekir, IIS 5.1 ve [!INCLUDE[iis601](../../../../includes/iis601-md.md)] yalnızca HTTP iletişimi için sınırlıdır. Bir barındırma ortamı seçme hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>IIS barındırılan bir WCF Hizmeti dağıtma  
 Geliştirme ve IIS barındırılan bir WCF Hizmeti dağıtma aşağıdaki görevleri içerir:  
  
-   IIS, ASP.NET, WCF ve WCF HTTP etkinleştirmesi bileşeni düzgün yüklü ve kayıtlı olan emin olun.  
  
-   Yeni bir IIS uygulama oluşturun veya mevcut bir yeniden [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
-   Bir WCF hizmeti için .svc dosyası oluşturun.  
  
-   Hizmet uygulaması için IIS uygulama dağıtın.  
  
-   WCF hizmetini yapılandırın.  
  
 Bu görevlerin her biri için bkz [Internet Information Services-Hosted bir WCF Hizmeti dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET  
 WCF hizmetleri olabilir ya da yan yana ile barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk Hizmetleri tarafından sağlanan özelliklerden tam anlamıyla gerçekleştirebileceğiniz modu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması platformu. Bu özellikler için bkz [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceHostFactory Kullanarak Barındırmayı Genişletme](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Internet Information Services Barındırma En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
