---
title: Özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: 4a6079db5e969154c4a9bb6451dd7c698c6d2088
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780377"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan bir sağlayıcılar kümesi içerir.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|Meta veri sağlayıcısı|Bu, <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> arabirimi uygulayarak çalışma zamanında özel bir veri modeli tanımlamanızı sağlayan temel özel veri hizmeti sağlayıcısıdır.|  
|Sorgu sağlayıcısı|Bu sağlayıcı, <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> arabirimi kullanılarak tanımlanan özel bir veri modeline karşı sorguları yürütmenizi sağlar. Sorgu sağlayıcısı, <xref:System.Data.Services.Providers.IDataServiceQueryProvider> arabirimini uygulayarak oluşturulur.|  
|Güncelleştirme sağlayıcısı|Bu sağlayıcı, özel bir veri hizmeti sağlayıcısında sunulan türlerde güncelleştirmeler yapmanızı ve eşzamanlılık yönetimini yapmanızı sağlar. <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> Arabirim uygulama tarafından bir güncelleştirme sağlayıcısı oluşturulur|  
|Sayfalama sağlayıcısı|Bu sağlayıcı, sunucu odaklı disk belleği desteğini etkinleştirmek için özel veri hizmeti sağlayıcısıyla birlikte kullanılır. Özel veri hizmeti için bir sayfalama sağlayıcısı, <xref:System.Data.Services.Providers.IDataServicePagingProvider> arabirimi uygulayarak oluşturulur.|  
|Akış sağlayıcısı|Bu sağlayıcı, ikili büyük nesne veri türlerini akış olarak kullanıma sunmanızı sağlar. Bir akış sağlayıcısı, <xref:System.Data.Services.Providers.IDataServiceStreamProvider> arabirimi uygulayarak oluşturulur. Akış sağlayıcısı ayrıca Entity Framework ve yansıma veri kaynağı sağlayıcılarıyla birlikte kullanılabilir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).|  
  
 Daha fazla bilgi için [OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069)'da [özel veri hizmeti sağlayıcıları](https://go.microsoft.com/fwlink/?LinkID=186850) ve [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] sağlayıcı araç seti makalesine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
