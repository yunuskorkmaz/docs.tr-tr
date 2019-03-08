---
title: başvuru bütünlüğü kısıtlaması
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 7d3304393ef4e97887d9b8afec94ed265e38eaf0
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679118"
---
# <a name="referential-integrity-constraint"></a>başvuru bütünlüğü kısıtlaması
A *başvuru bütünlüğü kısıtlaması* varlık veri modeli (EDM) ilişkisel bir veritabanındaki bir başvuru bütünlüğü kısıtlaması benzer. Bir veritabanı tablosundan bir sütuna (veya sütun) başka bir tablonun birincil anahtarı başvurabilirsiniz aynı şekilde bir [özelliği](../../../../docs/framework/data/adonet/property.md) (veya Özellikler), bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) başvurabilirsiniz [Varlık anahtarı ](../../../../docs/framework/data/adonet/entity-key.md) başka bir varlık türü. Başvurulan varlık türü olarak adlandırılır *birincil ucu* kısıtlaması. Birincil ucu başvuran varlık türü olarak adlandırılan *bağımlı son* kısıtlaması.  
  
 Başvuru bütünlük kısıtlamasının bir parçası olarak tanımlanan bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) iki varlık türleri arasında. Aşağıdaki bilgiler bir başvuru bütünlüğü kısıtlaması tanımını belirtir:  
  
-   Kısıtlamasının birincil ucu. (Varlık anahtarı bağımlı uç tarafından başvuruda bulunulan bir varlık türü.)  
  
-   Asıl son varlık anahtarı.  
  
-   Kısıtlamasının bağımlı bitiş olayı. (Bir özellik veya varlık anahtarı asıl bitiş başvurusu özellikleri içeren bir varlık türü.)  
  
-   Başvuruda bulunan özellik veya bağımlı bitiş özellikleri.  
  
 EDM başvuru bütünlüğü kısıtlamalarını amacı, geçerli bir ilişki her zaman var sağlamaktır. Daha fazla bilgi için [yabancı anahtar özelliği](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `WrittenBy` ve `PublishedBy`. `Book` Varlık türüne sahip bir özellik `PublisherId`, varlık anahtarı başvuran `Publisher` varlık türü bir başvuru bütünlüğü kısıtlaması tanımlarken `PublishedBy` ilişkilendirme.  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "başvuru kısıtlamasını model örneği")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Üzerinde bir başvuru bütünlüğü kısıtlaması aşağıdaki CSDL tanımlayan `PublishedBy` yukarıdaki kavramsal modelde gösterilen bir ilişkilendirme.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
