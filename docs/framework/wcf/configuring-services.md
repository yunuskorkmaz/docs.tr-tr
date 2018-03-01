---
title: "Hizmetleri Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 857ec77e54d6a55bde1a94fd9fd5758ef7a24309
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-services"></a>Hizmetleri Yapılandırma
Tasarlanmış ve hizmet sözleşmesini uygulanmış sonra hizmetiniz yapılandırmaya hazırsınız demektir. Burada tanımlayın ve hizmetinizi burada bulunabilir, taşıma ve iletileri ve gerektirdiği güvenlik türünü göndermek ve almak için kullandığı ileti kodlama adresini belirtme dahil olmak üzere istemcilere nasıl kullanıma sunulan özelleştirme budur.  
  
 Yapılandırma burada kullanılan gibi imperatively kodda veya tanımlama ve belirtme, uç nokta adresleri, kullanılan aktarımları ve kendi güvenlik düzenleri gibi bir hizmet çeşitli yönlerini özelleştirme bir yapılandırma dosyası kullanarak tüm yöntemleri içerir. Uygulamada, yazma yapılandırma programlama önemli bir parçası olan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)  
 İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kolaylaştıran yeni bir varsayılan yapılandırma modeli ile birlikte gelen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yapılandırma gereksinimleri. Herhangi bir belirtmezseniz, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] çalışma zamanı belirli bir hizmet yapılandırmasını varsayılan uç noktalar, bağlamaları ve davranışları hizmetinizi otomatik olarak yapılandırır.  
  
 [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmetidir yapılandırılabilir kullanarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknolojisi. XML öğeleri barındıran Internet Information Services (IIS) sitesi için Web.config dosyasının en yaygın olarak eklenen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet. Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek bir makine Makineli temelinde izin verin.  
  
 [Bağlamalar](../../../docs/framework/wcf/bindings.md)  
 Ayrıca, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hızlı bir şekilde nasıl bir istemci ve hizmet, aktarımları gibi güvenlik, iletişim için en temel özelliklerini seçmenize olanak tanır ve ileti Kodlamalar bağlamaları formunda birkaç sistem tarafından sağlanan ortak yapılandırmaları içerir kullanılır.  
  
 [Uç Noktalar](../../../docs/framework/wcf/endpoints.md)  
 İle tüm iletişimin bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] servis oluşur aracılığıyla *uç noktaları* hizmetinin. Uç noktaları sözleşme, bağlamaları belirtilen yapılandırma bilgilerini ve hizmet nerede bulacağını veya hizmeti hakkında bilgi almak nereye belirtmek adresleri içerir.  
  
 [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)  
 Kullanarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ve mevcut güvenlik mekanizmaları, gizlilik, bütünlük, kimlik doğrulama ve yetkilendirme herhangi bir hizmet uygulayabilirsiniz. Ayrıca, güvenlik başarı ve başarısızlık için de denetleyebilirsiniz.  
  
 [WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Birlikte çalışabilir hizmetler ve istemcileri herhangi bir platform veya işletim sistemi ile bir hizmeti dağıtma gereksinimleri WS özetlenen-ı temel Profil 1.1 belirtimini.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Kavramsal Genel Bakış](../../../docs/framework/wcf/conceptual-overview.md)  
 [WCF Özellik Ayrıntıları](../../../docs/framework/wcf/feature-details/index.md)
