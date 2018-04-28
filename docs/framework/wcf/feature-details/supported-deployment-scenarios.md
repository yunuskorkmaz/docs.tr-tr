---
title: Desteklenen Dağıtım Senaryoları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 82fa7e1b9619502dfdd27d2de29a502bec0af4f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="supported-deployment-scenarios"></a>Desteklenen Dağıtım Senaryoları
Alt kümesini [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kısmen güvenilir uygulamalar kullanımda kullanmak için ancak bazı değil tüm senaryoların gereksinimleri karşılamak üzere tasarlanmıştır için desteklenen özellikler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Sunucusunda, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] karşılıyor Internet ölçeğinde gereksinimlerini paylaşılan üçüncü taraf uygulamaları çalıştırmak barındırma hizmeti sağlayıcıları, [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Orta güven izni güvenlik nedenleriyle ayarlandı. İstemci üzerindeki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmi güven desteği gibi dağıtım teknolojileri gereksinimlerini karşılamak üzere tasarlanmıştır [ClickOnce dağıtımı](http://go.microsoft.com/fwlink/?LinkId=83712) veya [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]'s sorunsuz izin XAML tarayıcısı uygulaması teknoloji ve Masaüstü uygulamaları güvenilmeyen sitelerden güvenli dağıtımı.  
  
## <a name="minimum-permission-requirements"></a>Minimum izin gereksinimleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özelliklerinin bir kısmı ya da aşağıdaki standart adlandırılmış izin kümeleri altında çalışan uygulamaları destekler:  
  
-   Orta güven izinleri  
  
-   Internet bölgesi izinleri  
  
 Kullanılmaya çalışılıyor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] daha kısıtlayıcı izinlerle kısmen güvenilir uygulamalar çalışma zamanında güvenlik özel durumlarda neden olabilir.  
  
 Bu izin kümeleri desteklenen özellikler hakkında daha fazla bilgi için bkz: [kısmi güven özelliği uyumluluğu](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Sunucu üzerindeki kısmi güven  
 Birçok ticari sağlayıcılarından [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama Web barındırma hizmetleri sunucularında çalışan uygulamaların Çalıştır zorunluluğuna [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Orta güven izin kümesi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, bu ortamlarda çalıştırabilir, kullandıkları sağlanan <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, ya da <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> ile aktarım düzeyinde güvenlik.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] barındırma ortamları Medium Trust çalışan hizmetler, ayrıca diğer sunuculara istemci isteklerine yanıt iletileri göndererek orta katman hizmet olarak davranamaz. Barındırma ortamı uygulama uygun verildi, sunucuda orta katman senaryoları desteklenir <xref:System.Net.WebPermission> istenen sunucuya giden istekleri yapma.  
  
 Desteklenen SOAP bağlamaları birini kullanarak SOAP Mesajlaşma yanı sıra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekleyen <xref:System.ServiceModel.WebHttpBinding> Web stili Hizmetleri'nde kısmen güvenilir uygulamalar oluşturmak için. [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [WCF dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), ve [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) özelliklerini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] olan tüm kısmi güvende desteklenir.  
  
 İş akışı hizmetleri tam güven izinleri gerektirir ve kısmen güvenilir uygulamalar içinde kullanılamaz.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET 2.0 kullanım Medium Trust](http://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>İstemci üzerinde kısmi güven  
 Belirli güvenlik önlemleri indiriliyor ve güvenilmeyen Internet siteleriyle kod çalıştırırken alınması gerekir. Her ikisi de [ClickOnce dağıtımı](http://go.microsoft.com/fwlink/?LinkId=83712) ve [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]kullanıcının XAML tarayıcısı uygulaması (XBAP) teknolojisi olun kısmi güven sınırlı (Internet bölgesi) güvenilmeyen kod izinleri için kullanın.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmen güvenilir uygulamalar tarafından dağıtılan içinde uzak sunuculardan ile iletişim kurmak için kullanılan [ClickOnce dağıtımı](http://go.microsoft.com/fwlink/?LinkId=83712) veya XBAP. Internet bölgesi izin kümesi içerir <xref:System.Net.WebPermission> kaynak ana bilgisayar için sağlayan desteklenen birini kullanarak kendi kaynak sunucu ile iletişim kurmak bu uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamaları açıklanan [kısmi güven özelliği Uyumluluk](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod erişimi güvenliği](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation tarayıcıda barındırılan uygulamalar genel bakış](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [Kısmi Güven](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [ASP.Net Orta güven](http://go.microsoft.com/fwlink/?LinkId=69328)
