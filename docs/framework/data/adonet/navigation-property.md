---
title: Gezinme özelliği
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 149aefe84c9d04fab1786b99c2ac8c5060bccd87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="navigation-property"></a>Gezinme özelliği
A *gezinti özelliği* üzerinde isteğe bağlı bir özellik olan bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) izin veren bir gezinti için [son](../../../../docs/framework/data/adonet/association-end.md) , bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) için diğer sonu. Diğer aksine [özellikleri](../../../../docs/framework/data/adonet/property.md), gezinti özellikleri veri taşımak değil.  
  
 Bir gezinti özelliği tanımı aşağıdakileri içerir:  
  
-   Bir ad. (Gerekli)  
  
-   Bu gider ilişkilendirme. (Gerekli)  
  
-   Bu gider ilişkilendirme ucunun. (Gerekli)  
  
 Gezinti özellikleri her iki varlık türü bir ilişki ucundaki isteğe bağlı olduğunu unutmayın. Bir ilişkilendirme sonunda bir varlık türünde bir gezinti özelliği tanımlarsanız, ilişkinin diğer ucundaki varlık türünde bir gezinti özelliği tanımlamak gerekmez.  
  
 Veri türü bir gezinti özelliği tarafından belirlendiği [Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) kendi uzak [ilişki ucu](../../../../docs/framework/data/adonet/association-end.md). Örneğin, bir gezinti özelliği varsayalım `OrdersNavProp`, var. bir `Customer` varlık türü ve arasında bir-çok ilişkisi gider `Customer` ve `Order`. Gezinme özelliği için Uzak ilişkilendirme ucunun çokluğu birçok (*) sahip olduğundan, veri türü bir koleksiyonudur (biri `Order`). Benzer şekilde, bir gezinti özelliği, `CustomerNavProp`, var. `Order` varlık türü, veri türü olacaktır `Customer`, çünkü uzak ucunun çokluğu bir (1).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`. Gezinti özellikleri `Publisher` ve `Authors`, kitap varlık türünde tanımlanmış. Gezinti özelliği `Books` hem Yayımcı varlık türü üzerinde tanımlanan ve `Author` varlık türü.  
  
 ![Model Gezinti özellikleri ile](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterildiği varlık türü:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 XML öznitelikleri bir gezinti özelliği tanımlamak gerekli bilgileri iletişim kurmak için kullanılır unutmayın: öznitelik `Name` özelliğinin adını içeren `Relationship` , gider, ilişkilendirme adını içerir ve `FromRole` ve `ToRole` ilişkilendirme ucunun içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
