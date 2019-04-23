---
title: Entity Framework sağlayıcısı (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: a09c81b2d0f052884e8e54c899653a6f0e038aff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086253"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework sağlayıcısı (WCF Data Services)
Gibi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET varlık çerçevesi varlık verilerini bir tür varlık ilişkisi modeli olan modeli üzerinde temel alır. Entity Framework uygulaması çağrılır varlık veri modeli üzerinde işlemler çevirir *kavramsal model*, bir veri kaynağına karşı eşdeğer işlemler. Bu ideal bir sağlayıcı ilişkisel verilere dayalı Veri Hizmetleri için Entity Framework sağlar ve Entity Framework destekleyen bir veri sağlayıcısı sahip herhangi bir veritabanı ile birlikte kullanılabilir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Entity Framework destekleyen veri kaynaklarının listesi için bkz. [Entity Framework için üçüncü taraf sağlayıcılar](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Bir kavramsal modelde hizmet kök varlık kapsayıcıdır. Verileri bir veri hizmeti tarafından sunulabilir önce varlık Çerçevesi'nde bir kavramsal model tanımlamanız gerekir. Daha fazla bilgi için [nasıl yapılır: Bir ADO.NET varlık çerçevesi veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlık için eşzamanlı bir simge tanımlamak olanak tanıyarak iyimser eşzamanlılık modelini destekler. Bir veya daha fazla varlık özelliklerini içerir, bu eşzamanlılık belirteci, bir değişiklik, güncellenen veya silinen istenen verileri oluşup oluşmadığını belirlemek için veri hizmeti tarafından kullanılır. Varlığın geçerli değerlere eTag istekte alınan belirteç değerleri farklı olduğunda, bir özel durum veri hizmeti tarafından oluşturulur. Bir özellik eşzamanlılık belirtecinin bir parçası olduğundan, öznitelik uygulamalısınız belirtmek için `ConcurrencyMode="Fixed"` tarafından tanımlanan veri modelinde [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcısı. Eşzamanlılık belirteci, bir anahtar özellik ya da bir gezinti özelliği dahil edemezsiniz. Daha fazla bilgi için [veri hizmetini güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Varlık çerçevesi hakkında daha fazla bilgi için bkz: [Entity Framework'e Genel Bakış](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Yansıma Sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
