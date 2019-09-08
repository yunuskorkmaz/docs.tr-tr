---
title: Entity Framework sağlayıcısı (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 612888aaa11c606112527f01864897560061845f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790842"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework sağlayıcısı (WCF Veri Hizmetleri)
Benzer [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]şekilde, ADO.NET Entity Framework bir varlık ilişkisi modelinin türü olan varlık veri modeli temel alır. Entity Framework, işlemleri *kavramsal model*olarak adlandırılan varlık veri modeli uygulamasına karşı, bir veri kaynağına karşı eşdeğer işlemlere dönüştürür. Bu, Entity Framework ilişkisel verileri temel alan veri Hizmetleri için ideal bir sağlayıcı ve Entity Framework destekleyen bir veri sağlayıcısına sahip olan tüm veritabanları ile birlikte [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]kullanılabilir hale getirir. Entity Framework şu anda destekleyen veri kaynaklarının listesi için bkz. [Entity Framework Için üçüncü taraf sağlayıcıları](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Kavramsal modelde, varlık kapsayıcısı hizmetin köküdür. Verilerin bir veri hizmeti tarafından sunukullanabilmesi için önce Entity Framework bir kavramsal model tanımlamanız gerekir. Daha fazla bilgi için [nasıl yapılır: Bir ADO.NET Entity Framework veri kaynağı](create-a-data-service-using-an-adonet-ef-data-wcf.md)kullanarak veri hizmeti oluşturun.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir varlık için eşzamanlılık belirteci tanımlamanızı sağlayarak iyimser eşzamanlılık modelini destekler. Varlığın bir veya daha fazla özelliği içeren bu eşzamanlılık belirteci, istenen, güncellenen veya silinen verilerde bir değişikliğin oluşup oluşmadığını anlamak için veri hizmeti tarafından kullanılır. İstekteki eTag öğesinden alınan belirteç değerleri varlığın geçerli değerlerinden farklıysa, veri hizmeti tarafından bir özel durum oluşturulur. Bir özelliğin eşzamanlılık belirtecinin bir parçası olduğunu göstermek için özniteliği `ConcurrencyMode="Fixed"` [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcı tarafından tanımlanan veri modeline uygulamanız gerekir. Eşzamanlılık belirteci bir anahtar özellik veya bir gezinti özelliği içeremez. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Entity Framework hakkında daha fazla bilgi edinmek için bkz. [Entity Framework genel bakış](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
- [Varlık Veri Modeli](../adonet/entity-data-model.md)
