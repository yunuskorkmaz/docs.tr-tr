---
title: Gezinme özelliği
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 09c0e5e5dbc7b2be89e044c4d111fdd65fada7c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662185"
---
# <a name="navigation-property"></a>Gezinme özelliği
A *gezinti özelliği* üzerinde isteğe bağlı bir özellik olan bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) olanak tanıyan bir gezinti için [son](../../../../docs/framework/data/adonet/association-end.md) , bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) için diğer sonu. Diğer aksine [özellikleri](../../../../docs/framework/data/adonet/property.md), gezinti özellikleri veri taşıyan değil.  
  
 Bir gezinti özelliği tanımı aşağıdakileri içerir:  
  
-   Bir ad. (Gerekli)  
  
-   Bu varlıklardan ilişkilendirme. (Gerekli)  
  
-   Bu varlıklardan ilişkilendirmenin sona erer. (Gerekli)  
  
 Gezinti özellikleri her iki varlık türlerini ilişkilendirme ucunda isteğe bağlı olduğunu unutmayın. İlişkilendirme sonunda bir varlık türünün gezinme özelliğinin tanımlarsanız, ilişkinin diğer ucundaki varlık türünün gezinme özelliğinin tanımlamak zorunda değil.  
  
 Veri türü bir gezinti özelliği tarafından belirlenir [çoğulluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) kendi uzak [ilişkilendirme end](../../../../docs/framework/data/adonet/association-end.md). Örneğin, bir gezinti özelliği varsayalım `OrdersNavProp`, bulunuyor. bir `Customer` varlık türü ve arasında bir-çok ilişkisi gider `Customer` ve `Order`. Gezinti özelliği için Uzak ilişkilendirme end çokluğu birçok (*) olduğundan, kendi veri türüne bir koleksiyonudur (biri `Order`). Benzer şekilde, bir gezinti özelliği, `CustomerNavProp`, bulunuyor `Order` varlık türü, veri türü olacak `Customer`, uzak uç çokluğu bir (1) olduğundan.  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`. Gezinti özellikleri `Publisher` ve `Authors`, kitap varlık türünde tanımlanır. Gezinti özelliği `Books` hem Yayımcı varlık türü üzerinde tanımlanan ve `Author` varlık türü.  
  
 ![Gezinti özellikleri ile model](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterilen varlık türü:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 XML özniteliği bir gezinti özelliği tanımlamak gereken bilgileri iletişim kurmak için kullanıldığını unutmayın: Öznitelik `Name` özelliğin adını içeren `Relationship` bunu gider, ilişkilendirmenin adı içerir ve `FromRole` ve `ToRole` ilişki sonu içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
