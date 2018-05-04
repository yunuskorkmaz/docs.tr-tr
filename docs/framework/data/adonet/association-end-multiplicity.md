---
title: İlişki uç Çokluk
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 2f70fa4b163b957ea1e43506033863c3540b0418
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="association-end-multiplicity"></a>İlişki uç Çokluk
*İlişki uç Çokluk* sayısını tanımlar [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir sonunda olabilir örnekleri bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md).  
  
 Bir ilişkilendirme end Çokluk şu değerlerden biri olabilir:  
  
-   bir (1): Bu tam olarak bir varlık türü örneği var ilişkisi sonunda gösterir.  
  
-   sıfır veya bir (0.. 1 çokluğa): sıfır veya bir varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.  
  
-   birçok (*): sıfır, bir veya daha fazla varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.  
  
 Bir ilişkilendirme genellikle kendi ilişkilendirme son Çeşitlilikler tarafından belirlenir. Örneğin, bir ilişki uçlarından biri (1) ve çok sayıda Çeşitlilikler (*) varsa, ilişki bir-çok ilişkisi adı verilir. Aşağıdaki örnekte `PublishedBy` ilişkilendirmedir bir-çok ilişkisi (birçok books yayımcı yayımlar ve kitap bir yayımcı tarafından yayımlanan). `WrittenBy` İlişkilendirmedir bir çok-çok ilişkisi (kitap birden çok yazar olabilir ve bir yazar birden çok books yazabilirsiniz).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (*).  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) ADO.NET Entity Framework kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
