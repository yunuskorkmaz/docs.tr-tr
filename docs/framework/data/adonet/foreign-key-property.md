---
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: a77f7479ce38cb34830377021157f312916baca4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738402"
---
# <a name="foreign-key-property"></a>foreign key property
Varlık Veri Modeli (EDM) içindeki bir *yabancı anahtar özelliği* , başka bir varlık türünün [varlık anahtarını](entity-key.md) içeren bir [varlık türünde](entity-type.md) temel bir tür [özelliğidir](property.md) (veya ilkel tür özellikleri kümesi).  
  
 Yabancı anahtar özelliği, ilişkisel bir veritabanındaki yabancı anahtar sütunuyla benzerdir. Tablolar arasında bir ilişki oluşturmak için bir ilişkisel veritabanında yabancı anahtar sütunlarının kullanıldığı şekilde, varlık türleri arasında [ilişkilendirmeler](association-type.md) kurmak için kavramsal modeldeki yabancı anahtar özellikleri kullanılır. Türlerden birinde yabancı anahtar özelliği olduğunda iki varlık türü arasındaki ilişkiyi tanımlamak için bir [başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md) kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda üç varlık türü olan kavramsal bir model gösterilmektedir: `Book`, `Publisher`ve `Author`. `Book` varlık türü, `PublishedBy` ilişkilendirmesinde bir başvuru bütünlüğü kısıtlaması tanımlarken `Publisher` varlık türünün varlık anahtarına başvuran `PublisherId`bir özelliğe sahiptir.  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Başvuru kısıtlama modeli örneği")  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, yukarıda gösterilen kavramsal modelde gösterilen `PublishedBy` ilişkilendirmesinde bir başvurusal bütünlük kısıtlaması tanımlamak için `PublisherId` yabancı anahtar özelliğini kullanır.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
