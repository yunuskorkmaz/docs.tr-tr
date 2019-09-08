---
title: association end multiplicity
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cdcf69e7118620b2f8febd02d7695d429bf8cc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786950"
---
# <a name="association-end-multiplicity"></a>association end multiplicity
*Association End çoğulluğu* , [ilişkilendirmenin](association-type.md)bir ucunda olabilecek [varlık türü](entity-type.md) örneklerinin sayısını tanımlar.  
  
 Bir ilişkilendirme End çoğulluğu aşağıdaki değerlerden birine sahip olabilir:  
  
- bir (1): İlişki ucunda tam olarak bir varlık türü örneğinin bulunduğunu gösterir.  
  
- sıfır veya bir (0.. 1): İlişki ucunda sıfır veya bir varlık türü örneklerinin bulunduğunu belirtir.  
  
- Çok (\*): İlişkilendirme ucunda sıfır, bir veya daha fazla varlık türü örneğinin var olduğunu belirtir.  
  
 İlişki genellikle ilişkilendirme uç çarpanlarıyla belirlenir. Örneğin, bir ilişkinin uçları bir (1) ve çok (\*) çarpanlarına sahip olursa, ilişkilendirme bire çok ilişkilendirme olarak adlandırılır. Aşağıdaki örnekte, `PublishedBy` ilişkilendirme bire çok ilişkidir (yayımcı birçok kitabı yayınlar ve bir kitap tek bir yayımcı tarafından yayımlanır). `WrittenBy` İlişkilendirme çok-çok ilişkisi (bir kitapta birden çok yazar olabilir ve bir yazar birden çok kitap yazabilir).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve. `WrittenBy` İlişkilendirme için `PublishedBy` `Publisher` ilişkilendirme sonlanır `Book` ve varlık türleridir. `Publisher` Ucunun çoğulluğu bir (1), `Book` ucun çoğulluğu ise çok (\*).  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki alanına özgü DIL (DSL) kullanır. Aşağıdaki csdl, Yukarıdaki diyagramda `PublishedBy` gösterilen ilişkilendirmeyi tanımlar:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
