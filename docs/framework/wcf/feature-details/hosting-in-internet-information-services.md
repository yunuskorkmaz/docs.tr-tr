---
title: Internet Information Services'te Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 588e069280afc369256fdbee0132f732348ffc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-in-internet-information-services"></a>Internet Information Services'te Barındırma
Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir seçenek bir Internet Information Services (IIS) uygulama içinde bulunur. Bu barındırma modeli tarafından kullanılan model benzer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve ASP.NET Web Hizmetleri (ASMX) Web Hizmetleri.  
  
## <a name="versions-of-iis"></a>IIS sürümleri  
 WCF IIS'in aşağıdaki sürümleri aşağıdaki işletim sistemlerinde üzerinde barındırılabilir:  
  
-   IIS 5.1 üzerinde [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Bu ortamda tasarım ve daha sonra bir sunucu işletim sisteminde gibi dağıtılan IIS tarafından barındırılan uygulamalar geliştirme için yararlıdır [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] geliştirilmiş ölçeklenebilirlik, güvenilirlik ve uygulama yalıtımı sunan bir Gelişmiş işlem modeli sağlar. Bu ortamda, HTTP iletişimi için özel olarak kullanma WCF hizmetleri Üretim dağıtımı için uygundur.  
  
-   IIS 7.0 üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] ve [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. IIS 7.0 sağlar aynı Gelişmiş işlem modeli olarak [!INCLUDE[iis601](../../../../includes/iis601-md.md)], ancak HTTP dışındaki protokoller üzerinden etkinleştirme ve ağ iletişim sağlamak için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanır. Bu ortam (HTTP, net.tcp, net.pipe ve net.msmq dahil) WCF tarafından desteklenen herhangi bir ağ protokolü üzerinden iletişim WCF hizmetleri geliştirme için uygundur. WAS hakkında daha fazla bilgi için bkz: [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) çalışır [!INCLUDE[iisver](../../../../includes/iisver-md.md)] ve barındırma ortamı NET4 WCF ve WF Hizmetleri için zengin bir uygulama sağlamak için Windows İşlem Etkinleştirme Hizmeti (WAS). Bu, işlem yaşam döngüsü yönetimi, işlem geri dönüştürme, paylaşılan barındırma, hızlı hata koruması, işlem alt öğe Yitimi, isteğe bağlı etkinleştirme ve sistem durumu izleme yararları. Ayrıntılı bilgi için bkz: [AppFabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=196494) ve [AppFabric barındırma kavramları](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>IIS barındırma avantajları  
 IIS'de WCF hizmetlerini barındıran birkaç avantaj vardır:  
  
-   IIS barındırılan WCF hizmetleri dağıtılır ve tüm diğer IIS uygulamasının gibi yönetilen türü de dahil olmak üzere [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamaları ve ASMX.  
  
-   IIS işlem etkinleştirme, sistem yönetimi ve Geri Dönüşüm barındırılan uygulamalarının güvenilirliğini artırmak için özelliklerini sağlar.  
  
-   Gibi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], WCF hizmetleri barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] yararlanabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] birden çok uygulama bulunduğu geliştirilmiş sunucu yoğunluğu ve ölçeklenebilirlik için ortak bir çalışan işlemde paylaşılan barındırma modeli.  
  
-   IIS barındırılan WCF hizmetleri aynı dinamik derleme model olarak kullanmak [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], geliştirme basitleştirir ve dağıtımını barındırılan hizmetleri.  
  
 IIS'de WCF hizmetlerini barındırmak için karar verirken unutulmaması önemlidir; bu IIS 5.1 ve [!INCLUDE[iis601](../../../../includes/iis601-md.md)] yalnızca HTTP iletişimi için sınırlıdır. Bir barındırma ortamı seçme hakkında daha fazla bilgi için bkz: [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>IIS barındırılan bir WCF Hizmeti dağıtma  
 Geliştirme ve bir IIS tarafından barındırılan bir WCF Hizmeti dağıtma, aşağıdaki görevleri içerir:  
  
-   IIS, ASP.NET, WCF ve WCF HTTP etkinleştirmesi bileşeni düzgün yüklü ve kayıtlı olan emin olun.  
  
-   Yeni bir IIS uygulaması oluşturun veya varolan bir yeniden [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
-   WCF hizmeti için .svc dosyası oluşturun.  
  
-   Hizmet uygulaması için IIS uygulama dağıtın.  
  
-   WCF hizmetini yapılandırın.  
  
 Bu görevleri her bir tartışma için bkz: [Internet Information Services-Hosted WCF Hizmeti dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET  
 WCF hizmetleri olabilir ya da yan yana ile barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk Hizmetleri tarafından sağlanan özelliklerinden alabilir modu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması platformu. Bu özelliklerin tartışma için bkz [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceHostFactory Kullanarak Barındırmayı Genişletme](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Internet Information Services Barındırma En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
