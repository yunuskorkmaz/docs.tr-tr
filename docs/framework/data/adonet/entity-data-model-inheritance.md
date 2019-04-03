---
title: 'Varlık Veri Modeli: Devralma'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: bc0467ea1b242c13e00e115f07ccbc5c840df936
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837143"
---
# <a name="entity-data-model-inheritance"></a>Varlık Veri Modeli: Devralma
Varlık veri modeli (EDM) için devralmayı destekler [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md). EDM Devralmada nesne yönelimli programlama dillerinin sınıfların devralma benzer. Gibi dillerde nesne yönelimli sınıflarıyla kavramsal modelde bir varlık türü tanımlayabilirsiniz (bir *türetilmiş tür*) başka bir varlık türünden devralan ( *temel türü*). Ancak, nesne yönelimli programlama sınıflardan farklı olarak, kavramsal modelde türetilmiş tür her zaman tüm devralır [özellikleri](../../../../docs/framework/data/adonet/property.md) ve [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) temel türü. Türetilmiş bir tür devralınan özellikler geçersiz kılınamaz.  
  
 Kavramsal modelde, türetilmiş bir tür başka bir türetilmiş tür tarafından devralındığında devralma hiyerarşilerini oluşturabilirsiniz. (Bir türü türetilmiş bir tür değil hiyerarşide) hiyerarşinin üst türü olarak adlandırılır *kök türü*. Bir devralma hiyerarşisindeki [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) kök türü üzerinde tanımlanmış olması gerekir.  
  
 Türetilmiş bir tür birden fazla türünden devralan devralma hiyerarşilerini oluşturulamıyor. Kavramsal bir modelle, örneğin, bir `Book` varlık türü türetilen türlerin tanımlayabilirsiniz `FictionBook` ve `NonFictionBook` her kaynağından devraldığından `Book`. Ancak, daha sonra hem de devralan bir tür tanımlayabilirsiniz değil `FictionBook` ve `NonFictionBook` türleri.  
  
## <a name="example"></a>Örnek  

Aşağıdaki diyagramda dört varlık türleri kavramsal bir modelle gösterilmektedir: `Book`, `FictionBook`, `Publisher`, ve `Author`. `FictionBook` Varlık türü olduğu dan devralan türetilmiş bir tür `Book` varlık türü. `FictionBook` Tür devralır `ISBN (Key)`, `Title`, ve `Revision` özellikleri ve adlı ek bir özellik tanımlar `Genre`.  
  
 ![Kavramsal bir modelle dört varlık türlerini gösteren diyagram.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Bir varlık türü aşağıdaki CSDL tanımlar `FictionBook`, öğesinden devralan `Book` türü (örneğin, yukarıdaki diyagramda):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
