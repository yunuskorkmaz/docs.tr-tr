---
title: association type
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e75037223b235cf09df0bca85c6a4feb0b340174
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786898"
---
# <a name="association-type"></a>association type
İlişki *türü* (ilişki olarak da bilinir) VARLıK VERI MODELI (EDM) içindeki ilişkileri açıklamak için temel yapı taşdır. Kavramsal modelde, ilişki iki [varlık türü](entity-type.md) ( `Customer` ve `Order`gibi) arasındaki ilişkiyi temsil eder. Bir uygulamada, bir ilişkinin örneği belirli bir ilişkilendirmeyi temsil eder (bir `Customer` örneği ve bir `Order`örneği arasındaki ilişki gibi). İlişki örnekleri bir [ilişki kümesinde](association-set.md)mantıksal olarak gruplandırılır.  
  
 Bir ilişki tanımı aşağıdaki bilgileri içerir:  
  
- Benzersiz bir ad. Istenir  
  
- İlişki içindeki her varlık türü için bir tane olmak üzere iki [ilişkilendirme sonlanır](association-end.md). Istenir  
  
    > [!NOTE]
    > İlişki ikiden fazla varlık türü arasındaki ilişkiyi temsil edemez. Bununla birlikte bir ilişkilendirme, ilişki uçları her biri için aynı varlık türünü belirterek kendi kendine ilişki tanımlayabilir.  
  
- [Başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md). (İsteğe bağlı)  
  
 Her ilişkilendirme ucu, ilişkilendirmenin bir ucunda olabilecek varlık türü örneklerinin sayısını gösteren bir [ilişki ucu çeşitliliği](association-end-multiplicity.md) belirtmelidir. Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok (\*) değerine sahip olabilir. Bir ilişkinin bir sonundaki varlık türü örneklerine, bir varlık türü üzerinde gösterilmeleri durumunda [Gezinti özellikleri](navigation-property.md) veya yabancı anahtarlar üzerinden erişilebilir. Daha fazla bilgi için bkz [. varlık veri modeli: Yabancı anahtarlar](foreign-key-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve. `WrittenBy` İlişkilendirme için `PublishedBy` `Publisher` ilişkilendirme sonlanır `Book` ve varlık türleridir. `Publisher` Ucun çoğulluğu bir (1) ve `Book` ucun çoğulluğu birçok (\*), bir yayımcının çok sayıda kitap yayımladığını ve bir kitabın bir yayımcı tarafından yayımlandığını belirtir.  
  
 ![Üç varlık türüne sahip örnek model](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl, Yukarıdaki diyagramda `PublishedBy` gösterilen ilişkilendirmeyi tanımlar:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
