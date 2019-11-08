---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 3f3d8ba9f7e68065024dd3efb599b847496740cd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738575"
---
# <a name="association-end-multiplicity"></a>association end multiplicity
*Association End çoğulluğu* , [ilişkilendirmenin](association-type.md)bir ucunda olabilecek [varlık türü](entity-type.md) örneklerinin sayısını tanımlar.  
  
 Bir ilişkilendirme End çoğulluğu aşağıdaki değerlerden birine sahip olabilir:  
  
- bir (1): ilişkilendirme ucunda tam olarak bir varlık türü örneğinin bulunduğunu gösterir.  
  
- sıfır veya bir (0.. 1): ilişkilendirme ucunda sıfır veya bir varlık türü örneklerinin bulunduğunu belirtir.  
  
- Çok (\*): ilişkilendirme ucunda sıfır, bir veya daha fazla varlık türü örneğinin var olduğunu belirtir.  
  
 İlişki genellikle ilişkilendirme uç çarpanlarıyla belirlenir. Örneğin, bir ilişkinin uçları bir (1) ve birçok (\*) çarpanlarına sahip olursa, ilişkilendirme bire çok ilişkilendirme olarak adlandırılır. Aşağıdaki örnekte, `PublishedBy` ilişkilendirmesi bire çok ilişkidir (yayımcı birçok kitabı yayınlar ve bir kitap tek bir yayımcı tarafından yayımlanır). `WrittenBy` ilişkilendirmesi çoktan çoğa bir ilişkidir (bir kitapta birden çok yazar olabilir ve bir yazar birden çok kitap yazabilir).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip bir kavramsal model görülmektedir: `PublishedBy` ve `WrittenBy`. İlişki `PublishedBy` ilişkilendirme için sonlanır `Book` ve `Publisher` varlık türleridir. `Publisher` ucunun çoğulluğu bir (1), `Book` ucunun çokluğu ise çok (\*).  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki alanına özgü DIL (DSL) kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen `PublishedBy` ilişkilendirmesini tanımlar:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
