---
title: varlık türü
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 3955de1873d80e85df713a557750e34e76efeb41
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502890"
---
# <a name="entity-type"></a>varlık türü
*Varlık türü* varlık veri modeli (EDM) ile verilerin yapısını tanımlamak için temel yapı taşı. Kavramsal bir modeli içinde bir varlık türü müşteriler veya siparişler gibi üst düzey kavramlar yapısını temsil eder. Bir varlık türünün varlık türü örnekleri için bir şablondur. Her şablon, aşağıdaki bilgileri içerir:  
  
-   Benzersiz bir ad. (Gerekli)  
  
-   Bir [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) bir veya daha fazla özellikleri tarafından tanımlanan. (Gerekli)  
  
-   Veri biçiminde [özellikleri](../../../../docs/framework/data/adonet/property.md). (İsteğe bağlı.)  
  
-   [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) tanıyan bir gezinti için [son](../../../../docs/framework/data/adonet/association-end.md) , bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) diğer ucuna. (İsteğe bağlı)  
  
 Bir uygulamada (örneğin, belirli müşteri veya sipariş) belirli bir nesnesi bir varlık türünün bir örneği temsil eder. Bir varlık türünün her örneğinin benzersiz olmalıdır [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) içinde bir [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md).  
  
 İki varlık türü örnekleri yalnızca aynı türde oldukları ve bunların varlık anahtarları aynı değerleri eşit olarak kabul edilir.  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`:  
  
 ![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Her varlık türünün varlık anahtarıyla olun özellikleri "(anahtar)" ile belirtilir unutmayın.  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterilen varlık türü:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
- [facet](../../../../docs/framework/data/adonet/facet.md)
