---
title: Özel veri hizmeti sağlayıcıları (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: f198de20a3fa788fb8d5f2dc4ebf799989814756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765719"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Özel veri hizmeti sağlayıcıları (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan sağlayıcıları kümesini içerir.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|Meta veri sağlayıcısı|Bu uygulama tarafından çalışma zamanında bir özel veri modeli tanımlamanızı sağlayan temel özel veri hizmeti sağlayıcısı, <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> arabirimi.|  
|Sorgu sağlayıcısı|Bu sağlayıcı tarafından tanımlanan bir özel veri modeline karşı sorgular yürütün sağlayan <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> arabirimi. Uygulama tarafından oluşturulan sorgu sağlayıcısı <xref:System.Data.Services.Providers.IDataServiceQueryProvider> arabirimi.|  
|Güncelleştirme sağlayıcısı|Bu sağlayıcı bir özel veri hizmeti sağlayıcısı tarafından sunulan türleri güncelleştirmeler yapmak için ve eşzamanlılık yönetmenizi sağlar. Bir güncelleştirme sağlayıcısı uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> arabirimi|  
|Disk belleği sağlayıcısı|Bu sağlayıcı özel veri hizmeti sağlayıcısı ile sunucu tabanlı disk belleği desteğini etkinleştirmek için kullanılır. Özel veri hizmeti için bir disk belleği sağlayıcısı uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServicePagingProvider> arabirimi.|  
|Akış sağlayıcısı|Bu sağlayıcı ikili büyük nesne veri türlerini bir akış olarak kullanıma sunmanıza olanak sağlar. Akış sağlayıcısı uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServiceStreamProvider> arabirimi. Akış sağlayıcısı, Entity Framework ve yansıma veri kaynak sağlayıcıları ile de kullanılabilir. Daha fazla bilgi için [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
 Daha fazla bilgi için bkz [özel veri hizmeti sağlayıcılarını](https://go.microsoft.com/fwlink/?LinkID=186850) ve [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] sağlayıcısı araç setindeki [OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
- [Yansıma Sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
