---
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: e2f41c2db9aea26c7954a99ebf3f40b03e8df735
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795034"
---
# <a name="foreign-key-property"></a>foreign key property
Varlık Veri Modeli (EDM) içindeki bir *yabancı anahtar özelliği* , başka bir varlık türünün [varlık anahtarını](entity-key.md) içeren bir [varlık türünde](entity-type.md) temel bir tür [özelliğidir](property.md) (veya ilkel tür özellikleri kümesi).  
  
 Yabancı anahtar özelliği, ilişkisel bir veritabanındaki yabancı anahtar sütunuyla benzerdir. Tablolar arasında bir ilişki oluşturmak için bir ilişkisel veritabanında yabancı anahtar sütunlarının kullanıldığı şekilde, varlık türleri arasında [ilişkilendirmeler](association-type.md) kurmak için kavramsal modeldeki yabancı anahtar özellikleri kullanılır. Türlerden birinde yabancı anahtar özelliği olduğunda iki varlık türü arasındaki ilişkiyi tanımlamak için bir [başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md) kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book`, `Publisher`, ve `Author`. Varlık türü, `PublishedBy` ilişkide bir başvurusal bütünlük `PublisherId`kısıtlaması tanımlarken `Publisher` varlık türünün varlık anahtarına başvuran bir özelliğine sahiptir. `Book`  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Başvuru kısıtlama modeli örneği")  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl, yukarıda gösterilen kavramsal modelde gösterilen `PublisherId` `PublishedBy` ilişkide bir başvurusal bütünlük kısıtlaması tanımlamak için yabancı anahtar özelliğini kullanır.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
