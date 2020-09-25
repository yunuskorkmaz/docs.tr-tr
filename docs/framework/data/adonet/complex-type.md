---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: ef20de6a9e72d3123d745ef5501ecdb7fa63967d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203793"
---
# <a name="complex-type"></a>complex type

*Karmaşık tür* , [varlık türlerinde](entity-type.md) veya diğer karmaşık türlerde zengin, yapılandırılmış özellikleri tanımlamaya yönelik bir şablondur. Her şablon şunları içerir:  
  
- Benzersiz bir ad. Istenir  
  
    > [!NOTE]
    > Karmaşık bir türün adı aynı ad alanı içindeki bir varlık türü adı ile aynı olamaz.  
  
- Bir veya daha fazla [özellik](property.md)biçimindeki veriler. (İsteğe bağlı.)  
  
    > [!NOTE]
    > Karmaşık bir türün özelliği başka bir karmaşık tür olabilir.  
  
 Karmaşık bir tür, ilkel tür özellikleri veya diğer karmaşık türler biçiminde bir veri yükü taşıyamamakta olan bir varlık türüne benzerdir. Ancak, karmaşık türler ve varlık türleri arasında bazı önemli farklılıklar vardır:  
  
- Karmaşık türlerin kimlikleri yok ve bu nedenle bağımsız olarak bulunamaz. Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türlerde özellikler olarak bulunabilir.  
  
- Karmaşık türler [ilişkilendirmelere](association-type.md)katılamaz. İlişkinin sonu ne bir karmaşık tür olamaz, bu nedenle [Gezinti özellikleri](navigation-property.md) karmaşık türlerde tanımlanamaz.  
  
## <a name="example"></a>Örnek  

 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl,,,, ve basit tür özellikleriyle karmaşık bir tür, adres `StreetAddress` tanımlar `City` `StateOrProvince` `Country` `PostalCode` .  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Karmaşık türü `Address` (yukarıdaki) bir varlık türünde bir özellik olarak tanımlamak için, varlık türü tanımında Özellik türünü bildirmeniz gerekir. Aşağıdaki CSDL, `Address` özelliği bir varlık türü (yayımcı) üzerinde karmaşık bir tür olarak bildirir:  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
