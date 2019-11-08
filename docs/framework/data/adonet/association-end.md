---
title: association end
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 489802ca18708e076c0cd5dd380ad1361916ad5f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732363"
---
# <a name="association-end"></a>association end
Bir *ilişkilendirme End* 'i, [bir ilişkilendirmenin bir](association-type.md) sonundaki [varlık türünü](entity-type.md) ve bir ilişkinin o ucunda bulunabilir varlık türü örneklerinin sayısını tanımlar. İlişki uçları bir ilişkinin parçası olarak tanımlanır; bir ilişkilendirme tam olarak iki ilişkilendirme bitmelidir. [Gezinti özellikleri](navigation-property.md) , bir ilişkilendirme ucundan diğerine kadar gezinmesine izin verir.  
  
 Bir ilişkilendirme End tanımı aşağıdaki bilgileri içerir:  
  
- İlişkilendirmede yer alan varlık türlerinden biri. Istenir  
  
    > [!NOTE]
    > Belirli bir ilişki için, her ilişkilendirme ucu için belirtilen varlık türü aynı olabilir. Bu, kendine ilişkilendirme oluşturur.  
  
- İlişkilendirmenin bir ucunda olabilecek varlık türü örneklerinin sayısını gösteren bir [ilişkilendirme End çoğulluğu](association-end-multiplicity.md) . Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok (\*) bir değere sahip olabilir.  
  
- İlişki ucu için bir ad. (İsteğe bağlı)  
  
- İlişki ucunda gerçekleştirilen, silme sırasında Cascade gibi işlemler hakkında bilgiler. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip bir kavramsal model görülmektedir: `PublishedBy` ve `WrittenBy`. İlişki `PublishedBy` ilişkilendirme için sonlanır `Book` ve `Publisher` varlık türleridir. `Publisher` ucunun çoğulluğu bir (1) ve `Book` ucunun çoğulluğu birçok (\*) ve bir yayımcının çok sayıda kitabı yayımladığını ve bir yayımcının bir yayımcı tarafından yayımlandığını belirtir.  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki alanına özgü DIL (DSL) kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen `PublishedBy` ilişkilendirmesini tanımlar. Her ilişkilendirme ucunun türü, adı ve çeşitliliği XML öznitelikleri (sırasıyla `Type`, `Role`ve `Multiplicity` öznitelikleri) tarafından belirtilir. Bir uçta gerçekleştirilen işlemlerle ilgili isteğe bağlı bilgiler bir XML öğesinde (`OnDelete` öğesi) belirtilir. Bu durumda, bir yayımcı silinirse tüm ilişkili kitaplardır.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
