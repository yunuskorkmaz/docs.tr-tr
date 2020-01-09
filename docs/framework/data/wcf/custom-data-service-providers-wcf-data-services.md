---
title: Özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: a5041b04151a288f9c6c1a567dacec8da8c80a42
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346130"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan bir dizi sağlayıcı içerir.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|Meta veri sağlayıcısı|Bu, <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> arabirimini uygulayarak çalışma zamanında özel bir veri modeli tanımlamanızı sağlayan temel özel veri hizmeti sağlayıcısıdır.|  
|Sorgu sağlayıcısı|Bu sağlayıcı, <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> arabirimi kullanılarak tanımlanan özel bir veri modeline karşı sorguları yürütmenizi sağlar. Sorgu sağlayıcısı, <xref:System.Data.Services.Providers.IDataServiceQueryProvider> arabirimini uygulayarak oluşturulur.|  
|Güncelleştirme sağlayıcısı|Bu sağlayıcı, özel bir veri hizmeti sağlayıcısında sunulan türlerde güncelleştirmeler yapmanızı ve eşzamanlılık yönetimini yapmanızı sağlar. <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> arabirimi uygulama tarafından bir güncelleştirme sağlayıcısı oluşturulur|  
|Sayfalama sağlayıcısı|Bu sağlayıcı, sunucu odaklı disk belleği desteğini etkinleştirmek için özel veri hizmeti sağlayıcısıyla birlikte kullanılır. Özel veri hizmeti için bir sayfalama sağlayıcısı, <xref:System.Data.Services.Providers.IDataServicePagingProvider> arabirimi uygulayarak oluşturulur.|  
|Akış sağlayıcısı|Bu sağlayıcı, ikili büyük nesne veri türlerini akış olarak kullanıma sunmanızı sağlar. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> arabirimi uygulayarak bir akış sağlayıcısı oluşturulur. Akış sağlayıcısı ayrıca Entity Framework ve yansıma veri kaynağı sağlayıcılarıyla birlikte kullanılabilir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
