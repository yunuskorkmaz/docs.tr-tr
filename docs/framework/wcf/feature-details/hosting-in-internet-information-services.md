---
title: Internet Information Services'te Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 3940d8436ba5441d4e884879213a7a782214cb05
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486759"
---
# <a name="hosting-in-internet-information-services"></a>Internet Information Services'te Barındırma
Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir seçenek, içinde bir Internet Information Services (IIS) uygulamasıdır. Bu barındırma modeli, ASP.NET ve ASP.NET Web Hizmetleri (ASMX) Web Hizmetleri tarafından kullanılan modeline benzerdir.  
  
## <a name="versions-of-iis"></a>IIS sürümleri  
 WCF aşağıdaki işletim sistemlerinde aşağıdaki sürümlerinden birinde IIS üzerinde barındırılabilir:  
  
- IIS 5.1 [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Bu ortam tasarım ve daha sonra bir sunucu işletim sisteminde gibi dağıtılır, IIS tarafından barındırılan uygulamaların geliştirilmesini için kullanışlıdır [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
- IIS 6.0 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. IIS 6.0, geliştirilmiş ölçeklenebilirlik, güvenilirlik ve uygulama yalıtımı sunan bir Gelişmiş işlem modeli sağlar. Bu ortama, yalnızca HTTP iletişimi kullanan WCF hizmetleri Üretim dağıtımı için uygundur.  
  
- IIS 7.0 [!INCLUDE[wv](../../../../includes/wv-md.md)] ve [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. IIS 7.0, IIS 6.0 olarak aynı Gelişmiş işlem modeli sağlar, ancak etkinleştirme ve ağ iletişimi HTTP dışındaki protokoller üzerinden izin vermek için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanır. Bu ortam, WCF (HTTP, net.tcp, net.pipe ve net.msmq dahil) tarafından desteklenen herhangi bir ağ protokolü üzerinden iletişim kuran bir WCF hizmetleri geliştirmek için uygundur. WAS hakkında daha fazla bilgi için bkz: [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
- [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) IIS 7.0 ve Windows İşlem Etkinleştirme Hizmeti (WAS) barındırma ortamı ve WF NET4 WCF hizmetleri için zengin bir uygulama sağlamak için birlikte çalışır. Bu işlem yaşam döngüsü yönetimi, işlem geri dönüştürme, paylaşılan barındırma, hızlı hata koruması, işlem tek bırakma, isteğe bağlı etkinleştirme ve sistem durumu izleme avantajına sahip olur. Ayrıntılı bilgi için bkz. [AppFabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=196494) ve [AppFabric barındırma kavramları](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>IIS barındırma avantajları  
 WCF hizmetlerinde IIS barındırma birçok faydası vardır:  
  
- IIS barındırılan WCF hizmetleri dağıtılır ve başka türde ASP.NET uygulamalarını ve ASMX dahil olmak üzere, IIS uygulama gibi yönetilir.  
  
- IIS işlem etkinleştirme, sistem durumu yönetimi ve barındırılan uygulamaların güvenilirliğini artırmak için özellikler geri dönüştürme sağlar.  
  
- ASP.NET gibi birden çok uygulama geliştirilmiş sunucu yoğunluğu ve ölçeklenebilirlik için ortak bir çalışan işlemi bulunduğu ASP.NET'te barındırılan WCF hizmetleri ASP.NET paylaşılan barındırma modeli avantajlarından yararlanabilirsiniz.  
  
- IIS barındırılan WCF hizmetleri, geliştirme ve barındırılan hizmetlere dağıtımını basitleştiren ASP.NET 2.0 aynı dinamik derleme modelini kullanın.  
  
 WCF hizmetlerinde IIS konak karar verirken IIS 5.1 ve IIS 6. 0'ın yalnızca HTTP iletişimi için sınırlı olduğunu unutmamak önemlidir. Bir barındırma ortamı seçme hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>IIS barındırılan bir WCF Hizmeti dağıtma  
 Geliştirme ve IIS barındırılan bir WCF Hizmeti dağıtma aşağıdaki görevleri içerir:  
  
- IIS, ASP.NET, WCF ve WCF HTTP etkinleştirmesi bileşeni düzgün yüklü ve kayıtlı olan emin olun.  
  
- Yeni bir IIS uygulama oluşturun veya mevcut bir ASP.NET uygulamasını yeniden kullanabilirsiniz.  
  
- Bir WCF hizmeti için .svc dosyası oluşturun.  
  
- Hizmet uygulaması için IIS uygulama dağıtın.  
  
- WCF hizmetini yapılandırın.  
  
 Bu görevlerin her biri için bkz [Internet Information Services-Hosted bir WCF Hizmeti dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET  
 WCF hizmetleri olabilir ya da yan yana ASP.NET veya ASP.NET uyumluluk Hizmetleri ASP.NET Web uygulaması platform tarafından sağlanan özelliklerden tam anlamıyla gerçekleştirebileceğiniz modunda barındırılan. Bu özellikler için bkz [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceHostFactory Kullanarak Barındırmayı Genişletme](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Internet Information Services Barındırma En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
