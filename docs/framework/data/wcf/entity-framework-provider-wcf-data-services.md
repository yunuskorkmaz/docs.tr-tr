---
title: Entity Framework sağlayıcısı (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 0b6e76e6c05a091c57f27fc759044d3567cd976a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework sağlayıcısı (WCF Veri Hizmetleri)
Gibi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET Entity Framework varlık veri türü varlık ilişkisi modeli olan modelini, temel alır. Entity Framework adlandırılır varlık veri modeli uygulamaya karşı işlemleri çevirir *kavramsal model*, bir veri kaynağına karşı eşdeğer işlemlere. Bu Entity Framework ilişkisel verilere dayalı Veri Hizmetleri için ideal bir sağlayıcısı hale getirir ve Entity Framework destekleyen bir veri sağlayıcı olan herhangi bir veritabanı ile kullanılabilir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Entity Framework şu anda destekleyen veri kaynakları listesi için bkz: [üçüncü taraf sağlayıcılar için Entity Framework](http://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Bir kavramsal modelde hizmetinin kökü varlık kapsayıcıdır. Verileri bir veri hizmeti tarafından verilebilen önce Entity Framework kavramsal model tanımlamanız gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: bir ADO.NET Entity Framework veri kaynağına veri kullanarak hizmet oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlık için bir eşzamanlılık belirteci tanımlamanıza olanak sağlayarak iyimser eşzamanlılık modelini destekler. Bir veya daha fazla özellik varlık içerir, bu eşzamanlılık belirteci veri hizmeti tarafından bir değişiklik, güncellenen veya silinen istenen verilerde oluşup oluşmadığını belirlemek için kullanılır. Simge değerlerini istekte eTag alınan varlık geçerli değerlerden farklı bir özel durum veri hizmeti tarafından tetiklenir. Bir özellik eşzamanlılık belirteci parçası olan, öznitelik uygulamalısınız belirtmek için `ConcurrencyMode="Fixed"` tarafından tanımlanan veri modelindeki [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcısı. Eşzamanlılık belirteci bir anahtar özellik veya bir gezinti özelliği içeremez. Daha fazla bilgi için bkz: [veri hizmeti güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Entity Framework hakkında daha fazla bilgi için bkz: [Entity Framework genel bakış](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Yansıma Sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
