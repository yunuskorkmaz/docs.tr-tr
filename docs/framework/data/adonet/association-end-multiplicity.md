---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cf9e6b5af0dc6a33af364901c631b4ce66fe0480
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153514"
---
# <a name="association-end-multiplicity"></a>association end multiplicity

*Association End çoğulluğu* , [ilişkilendirmenin](association-type.md)bir ucunda olabilecek [varlık türü](entity-type.md) örneklerinin sayısını tanımlar.  
  
 Bir ilişkilendirme End çoğulluğu aşağıdaki değerlerden birine sahip olabilir:  
  
- bir (1): ilişkilendirme ucunda tam olarak bir varlık türü örneğinin bulunduğunu gösterir.  
  
- sıfır veya bir (0.. 1): ilişkilendirme ucunda sıfır veya bir varlık türü örneklerinin bulunduğunu belirtir.  
  
- Çok ( \* ): ilişkilendirme ucunda sıfır, bir veya daha fazla varlık türü örneğinin var olduğunu gösterir.  
  
 İlişki genellikle ilişkilendirme uç çarpanlarıyla belirlenir. Örneğin, bir ilişkinin uçları bir (1) ve çok () çarpanlarına sahip olursa \* , ilişkilendirme bire çok ilişkilendirme olarak adlandırılır. Aşağıdaki örnekte, `PublishedBy` ilişkilendirme bire çok ilişkidir (yayımcı birçok kitabı yayınlar ve bir kitap tek bir yayımcı tarafından yayımlanır). `WrittenBy`İlişkilendirme çok-çok ilişkisi (bir kitapta birden çok yazar olabilir ve bir yazar birden çok kitap yazabilir).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve `WrittenBy` . İlişkilendirme için ilişkilendirme sonlanır `PublishedBy` `Book` ve `Publisher` varlık türleridir. Ucunun çoğulluğu `Publisher` bir (1), ucun çoğulluğu ise `Book` çok ( \* ).  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki alanına özgü DIL (DSL) kullanır. Aşağıdaki CSDL, `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirmeyi tanımlar:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
