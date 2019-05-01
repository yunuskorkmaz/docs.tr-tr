---
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 74117b30ca54f7c57bd970003fc6f5dcc54d553f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879092"
---
# <a name="foreign-key-property"></a>foreign key property
A *yabancı anahtar özelliği* varlık veri modeli (EDM) basit bir türdür [özelliği](../../../../docs/framework/data/adonet/property.md) (veya basit tür özellikler kümesi) üzerinde bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) içeren[Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) başka bir varlık türü.  
  
 Bir yabancı anahtar özellik, ilişkisel bir veritabanındaki yabancı bir anahtar sütunu benzer. Yabancı anahtar sütunu satır tablolar arasındaki ilişkiler oluşturmak için ilişkisel bir veritabanında kullanılır aynı şekilde, kavramsal modelde yabancı anahtar özelliklerini oluşturmak için kullanılan [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md) varlık türleri arasında. A [başvuru bütünlüğü kısıtlaması](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) türlerinden birini bir yabancı anahtar özelliğine sahip iki varlık türleri arasındaki ilişkiyi tanımlamak için kullanılır.  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`. `Book` Varlık türüne sahip bir özellik `PublisherId`, varlık anahtarı başvuran `Publisher` varlık türü bir başvuru bütünlüğü kısıtlaması tanımlarken `PublishedBy` ilişkilendirme.  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "başvuru kısıtlamasını model örneği")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Yabancı anahtar özelliği aşağıdaki CSDL kullanan `PublisherId` bir başvuru bütünlüğü kısıtlaması tanımlamak için `PublishedBy` yukarıda gösterilen kavramsal modelde gösterilen bir ilişkilendirme.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
