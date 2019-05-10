---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: a6a7190a144280930d67f179373f29f6b19e98cc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583669"
---
# <a name="complex-type"></a>complex type
A *karmaşık tür* üzerinde zengin, yapısal özellikleri tanımlamak için bir şablon [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) veya diğer karmaşık türler. Her şablon şunları içerir:  
  
- Benzersiz bir ad. (Gerekli)  
  
    > [!NOTE]
    >  Karmaşık bir tür adı aynı ad alanı içinde bir varlık türü adı ile aynı olamaz.  
  
- Bir veya daha fazla bilgi formu verilerinde [özellikleri](../../../../docs/framework/data/adonet/property.md). (İsteğe bağlı.)  
  
    > [!NOTE]
    >  Karmaşık bir türün bir özelliği başka bir karmaşık türü olabilir.  
  
 Bir karmaşık türü bir veri yükü formun ilkel tür özellikleri veya diğer karmaşık türler taşıyabilir, bir karmaşık türü bir varlık türüne benzerdir. Ancak, karmaşık türlerden ve varlık türleri arasındaki bazı temel farklar vardır:  
  
- Karmaşık türler kimliklere sahip değildir ve bu nedenle bağımsız olarak var olamaz. Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türler özellikleri olarak bulunabilir.  
  
- Karmaşık türler içinde katılamaz [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md). Bir ilişkilendirmenin hiçbiri son karmaşık bir tür olabilir ve bu nedenle [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) karmaşık türlerde tanımlanamaz.  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL bir karmaşık tür adresi, ilkel türü özellikleri ile tanımlar `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Karmaşık tür tanımlamak için `Address` (yukarıda) bir varlık türü üzerindeki bir özellik olarak, özellik türü varlık tür tanımında bildirmeniz gerekir. Aşağıdaki CSDL bildirir `Address` özelliği bir varlık türü (yayımcı) üzerinde karmaşık bir tür olarak:  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
