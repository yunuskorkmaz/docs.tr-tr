---
title: Desteklenen Dağıtım Senaryoları
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: d0afd12b1c17f9356146aa13c90f8db65ed9ec0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="supported-deployment-scenarios"></a>Desteklenen Dağıtım Senaryoları
Kısmen güvenilir uygulamalar kullanmak için desteklenen Windows Communication Foundation (WCF) özellikleri alt WCF kullanma, ancak bazı değil tüm senaryoları gereksinimlerini karşılamak üzere tasarlanmıştır. Sunucuda, WCF karşılıyor Internet ölçeğinde gereksinimlerini paylaşılan üçüncü taraf uygulamaları çalıştırmak barındırma hizmeti sağlayıcıları, [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Orta güven izni güvenlik nedenleriyle ayarlandı. İstemcide, WCF kısmi güven desteği gibi dağıtım teknolojileri gereksinimlerini karşılamak üzere tasarlanmış [ClickOnce dağıtımı](http://go.microsoft.com/fwlink/?LinkId=83712) veya [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]'s sorunsuz ve güvenli izin XAML tarayıcısı uygulaması teknolojisi Masaüstü uygulamaları güvenilmeyen sitelerden dağıtımı.  
  
## <a name="minimum-permission-requirements"></a>Minimum izin gereksinimleri  
 WCF özelliklerinin bir kısmı ya da aşağıdaki standart adlandırılmış izin kümeleri altında çalışan uygulamaları destekler:  
  
-   Orta güven izinleri  
  
-   Internet bölgesi izinleri  
  
 Kısmen güvenilir uygulamalar daha kısıtlayıcı izinlerle WCF kullanmayı denemeden güvenlik özel durumları çalışma zamanında neden olabilir.  
  
 Bu izin kümeleri desteklenen özellikler hakkında daha fazla bilgi için bkz: [kısmi güven özelliği uyumluluğu](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Sunucu üzerindeki kısmi güven  
 Birçok ticari sağlayıcılarından [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama Web barındırma hizmetleri sunucularında çalışan uygulamaların Çalıştır zorunluluğuna [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Orta güven izin kümesi. WCF hizmetleri, bu ortamlarda çalıştırabilir, kullandıkları sağlanan <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, ya da <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> ile aktarım düzeyinde güvenlik.  
  
 Barındırma ortamları Medium Trust çalışan WCF hizmetleri, ayrıca diğer sunuculara istemci isteklerine yanıt iletileri göndererek orta katman hizmet olarak davranamaz. Barındırma ortamı uygulama uygun verildi, sunucuda orta katman senaryoları desteklenir <xref:System.Net.WebPermission> istenen sunucuya giden istekleri yapma.  
  
 Desteklenen SOAP bağlamaları birini kullanarak SOAP Mesajlaşma ek olarak, WCF destekleyen <xref:System.ServiceModel.WebHttpBinding> Web stili Hizmetleri'nde kısmen güvenilir uygulamalar oluşturmak için. [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [WCF dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), ve [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) özellikleri WCF tüm desteklenmektedir kısmi güven.  
  
 İş akışı hizmetleri tam güven izinleri gerektirir ve kısmen güvenilir uygulamalar içinde kullanılamaz.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET 2.0 kullanım Medium Trust](http://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>İstemci üzerinde kısmi güven  
 Belirli güvenlik önlemleri indiriliyor ve güvenilmeyen Internet siteleriyle kod çalıştırırken alınması gerekir. Her ikisi de [ClickOnce dağıtımı](http://go.microsoft.com/fwlink/?LinkId=83712) ve [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]kullanıcının XAML tarayıcısı uygulaması (XBAP) teknolojisi olun kısmi güven sınırlı (Internet bölgesi) güvenilmeyen kod izinleri için kullanın.  
  
 WCF tarafından dağıtılan kısmen güvenilir uygulamalar içinde uzak sunuculardan ile iletişim kurmak için kullanılabilir [ClickOnce dağıtımı](http://go.microsoft.com/fwlink/?LinkId=83712) veya XBAP. Internet bölgesi izin kümesi içerir <xref:System.Net.WebPermission> kaynak ana bilgisayar için sağlayan açıklanan desteklenen WCF bağlamaları birini kullanarak kendi kaynak sunucu ile iletişim kurmak bu uygulamaları [kısmi güven özelliği uyumluluğu ](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod erişimi güvenliği](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation tarayıcıda barındırılan uygulamalar genel bakış](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [Kısmi Güven](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [ASP.Net Orta güven](http://go.microsoft.com/fwlink/?LinkId=69328)
