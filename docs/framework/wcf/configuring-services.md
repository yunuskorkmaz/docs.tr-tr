---
title: WCF hizmetlerini yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 2435d5c4592de60e07b60f1bf749f2421c798535
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303625"
---
# <a name="configuring-wcf-services"></a>WCF hizmetlerini yapılandırma

Tasarlanmış ve hizmet sözleşmeniz uygulanan sonra hizmetinizin yapılandırmaya hazırsınız. Burada tanımlayın ve hizmetinizi burada bulunabilir, taşıma ve iletileri ve gerektiren güvenlik türünü göndermek ve almak için kullandığı ileti kodlama adresi belirtme dahil olmak üzere istemcilere nasıl kullanıma sunulan özelleştirme budur.  
  
 Yapılandırma burada kullanılan kesin kod veya tanımlayın ve bir hizmetin kendi güvenlik düzenleri, uç nokta adresleri ve kullanılan taşımalar belirleme gibi çeşitli yönlerini de özelleştirerek bir yapılandırma dosyası kullanarak tüm yöntemleri içerir. Büyük bir uygulamada, yazma yapılandırmadır WCF uygulamalarını programlama parçası.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)  
 İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, WCF yapılandırma gereksinimleri basitleştiren yeni bir varsayılan yapılandırma modeli ile birlikte gelir. Belirli bir hizmet için herhangi bir WCF yapılandırma sağlamazsanız, çalışma zamanı varsayılan uç noktaları, bağlamalar ve davranışları ile otomatik olarak hizmetinizi yapılandırır.  
  
 [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Yapılandırılabilir kullanarak bir Windows Communication Foundation (WCF) hizmetidir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknoloji. En yaygın olarak, XML öğeleri, bir WCF hizmetini barındıran Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir. Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek makine tarafından makine olarak sağlar.  
  
 [Bağlamalar](../../../docs/framework/wcf/bindings.md)  
 Ayrıca, WCF, hızlı bir şekilde nasıl bir istemci ve hizmet iletişim kurmak için aktarımlar, güvenlik ve kodlamaları kullanılan ileti gibi en temel özellikler seçmenizi sağlayacak bağlamaları biçiminde birçok sistem tarafından sağlanan genel yapılandırmaları içerir.  
  
 [Uç Noktalar](../../../docs/framework/wcf/endpoints.md)  
 Bir WCF Hizmeti ile tüm iletişimi üzerinden gerçekleşir *uç noktaları* hizmeti. Uç noktaları, sözleşmenin bağlamaları belirtilen yapılandırma bilgilerini ve hizmet nerede bulacağını veya hizmet hakkında bilgi almak nereye belirtmek adresleri içerir.  
  
 [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)  
 WCF kullanan ve var olan güvenlik mekanizmaları, gizlilik, bütünlük, kimlik doğrulama ve yetkilendirme, herhangi bir hizmet uygulayabilirsiniz. Ayrıca, güvenlik başarı ve başarısızlık için de denetleyebilirsiniz.  
  
 [WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Hizmetler ve istemcileri herhangi bir platform veya işletim sistemi ile birlikte çalışabilen bir hizmeti dağıtmak için gereksinimleri WS içinde ana hatlarıyla özetlenen-ı Basic Profile 1.1 belirtimi.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Temel Programlama Yaşam Döngüsü](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Hizmetleri Tasarlama ve Uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Barındırma Hizmetleri](../../../docs/framework/wcf/hosting-services.md)  
  
 [İstemci Derleme](../../../docs/framework/wcf/building-clients.md)  
  
 [Genişletilebilirliğe Genel Bakış](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Yönetim ve Tanılama](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Kavramsal Genel Bakış](../../../docs/framework/wcf/conceptual-overview.md)
- [WCF Özellik Ayrıntıları](../../../docs/framework/wcf/feature-details/index.md)
