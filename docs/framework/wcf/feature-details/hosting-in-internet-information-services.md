---
title: "Internet Information Services'te Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 988216447e47345b6d863de6e46d0de9a025f068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-internet-information-services"></a>Internet Information Services'te Barındırma
Barındırma için bir seçenek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri olan bir Internet Information Services (IIS) uygulama içinde. Bu barındırma modeli tarafından kullanılan model benzer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve ASP.NET Web Hizmetleri (ASMX) Web Hizmetleri.  
  
## <a name="versions-of-iis"></a>IIS sürümleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS aşağıdaki sürümleri aşağıdaki işletim sistemlerinde üzerinde barındırılabilir:  
  
-   IIS 5.1 üzerinde [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Bu ortamda tasarım ve daha sonra bir sunucu işletim sisteminde gibi dağıtılan IIS tarafından barındırılan uygulamalar geliştirme için yararlıdır [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)]üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)]geliştirilmiş ölçeklenebilirlik, güvenilirlik ve uygulama yalıtımı sunan bir Gelişmiş işlem modeli sağlar. Bu ortam Üretim dağıtımı için uygun olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP iletişimi için özel olarak kullanan hizmetler.  
  
-   IIS 7.0 üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] ve [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. IIS 7.0 sağlar aynı Gelişmiş işlem modeli olarak [!INCLUDE[iis601](../../../../includes/iis601-md.md)], ancak HTTP dışındaki protokoller üzerinden etkinleştirme ve ağ iletişim sağlamak için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanır. Bu ortamda geliştirme için uygun olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] herhangi iletişim hizmetleri protokolü tarafından desteklenen ağ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (HTTP, net.tcp, net.pipe ve net.msmq dahil). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]TAKDİRDE bkz [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) çalışır [!INCLUDE[iisver](../../../../includes/iisver-md.md)] ve barındırma ortamı NET4 WCF ve WF Hizmetleri için zengin bir uygulama sağlamak için Windows İşlem Etkinleştirme Hizmeti (WAS). Bu, işlem yaşam döngüsü yönetimi, işlem geri dönüştürme, paylaşılan barındırma, hızlı hata koruması, işlem alt öğe Yitimi, isteğe bağlı etkinleştirme ve sistem durumu izleme yararları. Ayrıntılı bilgi için bkz: [AppFabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=196494) ve [AppFabric barındırma kavramları](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>IIS barındırma avantajları  
 Barındırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetlerinin IIS'de çeşitli avantajları vardır:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS barındırılan hizmetleri dağıtılır ve tüm diğer IIS uygulamasının gibi yönetilen türü de dahil olmak üzere [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamaları ve ASMX.  
  
-   IIS işlem etkinleştirme, sistem yönetimi ve Geri Dönüşüm barındırılan uygulamalarının güvenilirliğini artırmak için özelliklerini sağlar.  
  
-   Gibi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] barındırılan hizmetlere [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] yararlanabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] birden çok uygulama bulunduğu geliştirilmiş sunucu yoğunluğu ve ölçeklenebilirlik için ortak bir çalışan işlemde paylaşılan barındırma modeli.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS barındırılan hizmetleri aynı dinamik derleme model olarak kullanmak [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], geliştirme basitleştirir ve dağıtımını barındırılan hizmetleri.  
  
 Karar verirken ana bilgisayara [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetlerinin IIS'de olduğu unutulmamalıdır, IIS 5.1 ve [!INCLUDE[iis601](../../../../includes/iis601-md.md)] yalnızca HTTP iletişimi için sınırlıdır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bir barındırma ortamı seçme, bkz: [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>IIS barındırılan bir WCF Hizmeti dağıtma  
 Geliştirme ve bir IIS tarafından barındırılan dağıtma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, aşağıdaki görevleri içerir:  
  
-   Sağlamak bu IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP etkinleştirme bileşeni doğru yüklendiğinden ve kayıtlı.  
  
-   Yeni bir IIS uygulaması oluşturun veya varolan bir yeniden [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
-   İçin bir .svc dosyası oluşturmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
-   Hizmet uygulaması için IIS uygulama dağıtın.  
  
-   Yapılandırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 Bu görevleri her bir tartışma için bkz: [Internet Information Services-Hosted WCF Hizmeti dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hizmetleri olabilir ya da yan yana ile barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk Hizmetleri tarafından sağlanan özelliklerinden alabilir modu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması platformu. Bu özelliklerin tartışma için bkz [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceHostFactory Kullanarak Barındırmayı Genişletme](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Internet Information Services Barındırma En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
