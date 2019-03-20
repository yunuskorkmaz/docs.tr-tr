---
title: İlişki sonu çeşitlilik
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 151b15a6df021a25f6c3ecea00af147c6b7196ff
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185681"
---
# <a name="association-end-multiplicity"></a>İlişki sonu çeşitlilik
*İlişki sonu çoğulluk* sayısını tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir sonunda olabilir örnekleri bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md).  
  
 Bir ilişkilendirme end çoğulluk aşağıdaki değerlerden biri olabilir:  
  
-   bir (1): Bu tam olarak bir varlık türü örneği ilişkilendirme sonunda olup olmadığını gösterir.  
  
-   sıfır veya bir (0..1): Sıfır veya bir varlık türü örneklerini ilişkilendirme sonunda bulunduğunu gösterir.  
  
-   çok sayıda (\*): sıfır, bir veya daha fazla varlık türü örneklerini ilişkilendirme sonunda bulunduğunu gösterir.  
  
 Bir ilişkilendirme genellikle, ilişki uç Çeşitlilikler tarafından belirlenir. Örneğin, bir ilişki sonu bir (1) ve çok sayıda Çeşitlilikler varsa (\*), ilişkilendirmenin bir-çok ilişkisi adı verilir. Aşağıdaki örnekte `PublishedBy` işbirliğidir bir-çok ilişkisi (bir çok kitap bir yayımcı yayımlar ve bir kitap bir yayımcı tarafından yayımlanır). `WrittenBy` Bir çoktan çoğa ilişki bir ilişkilendirmedir (bir kitap birden çok yazarlar olabilir ve birden çok books Yazar yazabilirsiniz).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona için `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çeşitliliğini `Book` sonudur birçok (\*).  
  
 ![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET varlık çerçevesi kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkiyi:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
