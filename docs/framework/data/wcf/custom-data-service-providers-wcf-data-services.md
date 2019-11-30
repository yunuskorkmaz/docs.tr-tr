---
title: Özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: c5f6bd001a5198f14bf05c0730f3988d54142eae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569243"
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
  
 Daha fazla bilgi için [OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069)'Da [özel veri hizmeti sağlayıcıları](https://go.microsoft.com/fwlink/?LinkID=186850) ve açık veri Protokolü (OData) sağlayıcı araç seti makalesine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
