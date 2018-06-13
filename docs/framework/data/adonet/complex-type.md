---
title: karmaşık türü
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 8daeac8309434b3c4e090d8e75f2de02d63e8b11
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756819"
---
# <a name="complex-type"></a>karmaşık türü
A *karmaşık tür* üzerinde zengin, yapılandırılmış özelliklerini tanımlamak için bir şablon [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) veya başka karmaşık türler. Her bir şablon aşağıdakileri içerir:  
  
-   Benzersiz bir ad. (Gerekli)  
  
    > [!NOTE]
    >  Karmaşık bir tür adı aynı ad alanı içindeki bir varlık türü adı ile aynı olamaz.  
  
-   Bir veya daha fazla form verileri [özellikleri](../../../../docs/framework/data/adonet/property.md). (İsteğe bağlı.)  
  
    > [!NOTE]
    >  Karmaşık türde bir özellik, başka bir karmaşık tür olabilir.  
  
 Karmaşık bir tür, karmaşık bir tür veri yükü ilkel tür özellikleri biçiminde veya başka karmaşık türler taşıyabilir, bir varlık türüne benzerdir. Ancak, karmaşık türleri ve varlık türleri arasındaki bazı temel farklar vardır:  
  
-   Karmaşık türler kimliklerine sahip değil ve bu nedenle bağımsız olarak bulunamaz. Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türler özellikleri olarak bulunabilir.  
  
-   Karmaşık türler olamaz katılmak [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md). Bir ilişkilendirme hiçbiri sonuna bir karmaşık tür olabilir ve bu nedenle [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) karmaşık türlerinde tanımlanamaz.  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL bir karmaşık türü, adres, ilkel türü özellikleri ile tanımlayan `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Karmaşık türü tanımlamak için `Address` (yukarıda) bir varlık türünde bir özellik olarak, özellik türü varlık türü tanımında belirtmesi gerekir. Aşağıdaki CSDL bildirir `Address` özelliği bir karmaşık tür üzerinde bir varlık türü (yayımcı) olarak:  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
