---
title: Desteklenen Dağıtım Senaryoları
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: a86fd9d50b2bdfa2daafa3bec98802d10a1efef5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672624"
---
# <a name="supported-deployment-scenarios"></a>Desteklenen Dağıtım Senaryoları
Kısmen güvenilir uygulamaların kullanım için desteklenen Windows Communication Foundation (WCF) özellikleri alt kümesi için WCF kullanan bazı, tümü değil, senaryolar gereksinimlerini karşılamak üzere tasarlanmıştır. Sunucuda, WCF karşıladığını Internet ölçeğinde gereksinimlerini paylaşılan üçüncü taraf uygulamaları barındırma sağlayıcıları, [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Medium Trust izni güvenlik nedenleriyle ayarlayın. İstemcide, WCF kısmi güven desteği gibi dağıtım teknolojileri gereksinimlerini karşılamak için tasarlanan [ClickOnce dağıtımı](https://go.microsoft.com/fwlink/?LinkId=83712) veya [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]'s XAML tarayıcı uygulaması teknolojisi, sorunsuz ve güvenli izin ver güvenilmeyen siteleri'ndan Masaüstü uygulamaların dağıtımı.  
  
## <a name="minimum-permission-requirements"></a>En düşük izin gereksinimleri  
 WCF ya da aşağıdaki standart adlandırılmış izin kümelerinin altında çalışan uygulamalar, özelliklerin bir alt kümesini destekler:  
  
-   Orta güven izinleri  
  
-   Internet bölgesi izinleri  
  
 Kısmen güvenilir uygulamaların daha kısıtlayıcı izinlerle WCF kullanma girişimi çalışma zamanında güvenlik özel durumları neden olabilir.  
  
 Bu izin kümeleri, desteklenen özellikler hakkında daha fazla bilgi için bkz: [kısmi güven özelliği uyumluluğu](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Sunucu üzerinde kısmi güven  
 Birçok ticari sağlayıcılardan biri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulama barındırma hizmetleri, sunucuları üzerinde çalışan uygulamaları çalıştırmak olan uyumluluğunu doğrulamıştır [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] Medium Trust izin kümesi. WCF hizmetleri, bu ortamlarda çalıştırabilirsiniz, kullandıkları sağlanan <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, ya da <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> aktarım düzeyi güvenlik ile.  
  
 WCF hizmetlerini barındırma ortamları Medium Trust ile çalışan istemci isteklerine yanıt diğer sunuculara yönelik iletiler göndererek orta katman hizmet olarak da işlev görebilir. Uygulama barındırma ortamı uygun izni vermiştir, orta katman senaryoları sunucuda desteklenir <xref:System.Net.WebPermission> istedikleri sunucuya giden isteklerde.  
  
 Desteklenen SOAP bağlamaları birini kullanarak SOAP ileti ek olarak, WCF destekler <xref:System.ServiceModel.WebHttpBinding> kısmen güvenilir uygulamaların stili Web hizmetleri oluşturmak için. [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [WCF dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), ve [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) WCF özelliklerinin tümü desteklenir kısmi güven.  
  
 İş akışı Hizmetleri, tam güven izinleri gerektirir ve kısmen güvenilen uygulamalarda kullanılamaz.  
  
 Daha fazla bilgi için [nasıl yapılır: ASP.NET 2.0 kullanım Orta güven](https://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>İstemci üzerinde kısmi güven  
 Belirli güvenlik önlemleri indiriliyor ve güvenilmeyen Internet siteleriyle kod çalıştırırken alınması gerekir. Her ikisi de [ClickOnce dağıtımı](https://go.microsoft.com/fwlink/?LinkId=83712) ve [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]kullanıcının teknoloji olun XAML tarayıcı uygulaması (XBAP) kullanın kısmi güven güvenilmeyen kod (Internet bölgesi) sınırlı izinler vermek için.  
  
 WCF tarafından dağıtılan kısmen güvenilir uygulamaların içinde uzak sunuculardan ile iletişim kurmak için kullanılabilir [ClickOnce dağıtımı](https://go.microsoft.com/fwlink/?LinkId=83712) veya XBAP. Internet bölgesi izin kümesi içeren <xref:System.Net.WebPermission> kaynak konağını sağlayan açıklanan desteklenen WCF bağlamaları birini kullanarak, kaynak sunucu ile iletişim kurmak bu uygulamaları [kısmi güven özelliği uyumluluğu ](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod erişimi güvenliği](https://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation tarayıcıda tutulan uygulamalar genel bakış](https://go.microsoft.com/fwlink/?LinkId=98397)  
 [Kısmi Güven](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [ASP.Net Orta güven](https://go.microsoft.com/fwlink/?LinkId=69328)
