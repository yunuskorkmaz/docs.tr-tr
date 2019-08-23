---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: fac25ace69938e1245200e10285f4460ac216780
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948725"
---
# <a name="complex-type"></a>complex type
*Karmaşık tür* , [varlık türlerinde](../../../../docs/framework/data/adonet/entity-type.md) veya diğer karmaşık türlerde zengin, yapılandırılmış özellikleri tanımlamaya yönelik bir şablondur. Her şablon şunları içerir:  
  
- Benzersiz bir ad. Istenir  
  
    > [!NOTE]
    > Karmaşık bir türün adı aynı ad alanı içindeki bir varlık türü adı ile aynı olamaz.  
  
- Bir veya daha fazla [özellik](../../../../docs/framework/data/adonet/property.md)biçimindeki veriler. (İsteğe bağlı.)  
  
    > [!NOTE]
    > Karmaşık bir türün özelliği başka bir karmaşık tür olabilir.  
  
 Karmaşık bir tür, ilkel tür özellikleri veya diğer karmaşık türler biçiminde bir veri yükü taşıyamamakta olan bir varlık türüne benzerdir. Ancak, karmaşık türler ve varlık türleri arasında bazı önemli farklılıklar vardır:  
  
- Karmaşık türlerin kimlikleri yok ve bu nedenle bağımsız olarak bulunamaz. Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türlerde özellikler olarak bulunabilir.  
  
- Karmaşık türler [ilişkilendirmelere](../../../../docs/framework/data/adonet/association-type.md)katılamaz. İlişkinin sonu ne bir karmaşık tür olamaz, bu nedenle [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) karmaşık türlerde tanımlanamaz.  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl,,,, ve `StreetAddress` `StateOrProvince` `City` `Country` basittürözellikleriylekarmaşıkbirtür,adrestanımlar.`PostalCode`  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Karmaşık türü `Address` (yukarıdaki) bir varlık türünde bir özellik olarak tanımlamak için, varlık türü tanımında Özellik türünü bildirmeniz gerekir. Aşağıdaki csdl, `Address` özelliği bir varlık türü (yayımcı) üzerinde karmaşık bir tür olarak bildirir:  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
