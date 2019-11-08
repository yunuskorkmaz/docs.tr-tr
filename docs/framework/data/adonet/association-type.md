---
title: association type
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e1430e6255dce2bae6d82411db5d2a9f11f46e1a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738561"
---
# <a name="association-type"></a>association type
İlişki *türü* (ilişki olarak da bilinir) VARLıK VERI MODELI (EDM) içindeki ilişkileri açıklamak için temel yapı taşdır. Kavramsal modelde, ilişki iki [varlık türü](entity-type.md) arasındaki ilişkiyi temsil eder (`Customer` ve `Order`gibi). Bir uygulamada, bir ilişkinin örneği belirli bir ilişkilendirmeyi temsil eder (bir `Customer` örneği ve bir `Order`örneği arasındaki ilişki gibi). İlişki örnekleri bir [ilişki kümesinde](association-set.md)mantıksal olarak gruplandırılır.  
  
 Bir ilişki tanımı aşağıdaki bilgileri içerir:  
  
- Benzersiz bir ad. Istenir  
  
- İlişki içindeki her varlık türü için bir tane olmak üzere iki [ilişkilendirme sonlanır](association-end.md). Istenir  
  
    > [!NOTE]
    > İlişki ikiden fazla varlık türü arasındaki ilişkiyi temsil edemez. Bununla birlikte bir ilişkilendirme, ilişki uçları her biri için aynı varlık türünü belirterek kendi kendine ilişki tanımlayabilir.  
  
- [Başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md). (İsteğe bağlı)  
  
 Her ilişkilendirme ucu, ilişkilendirmenin bir ucunda olabilecek varlık türü örneklerinin sayısını gösteren bir [ilişki ucu çeşitliliği](association-end-multiplicity.md) belirtmelidir. Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok (\*) bir değere sahip olabilir. Bir ilişkinin bir sonundaki varlık türü örneklerine, bir varlık türü üzerinde gösterilmeleri durumunda [Gezinti özellikleri](navigation-property.md) veya yabancı anahtarlar üzerinden erişilebilir. Daha fazla bilgi için bkz. [varlık veri modeli: yabancı anahtarlar](foreign-key-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip bir kavramsal model görülmektedir: `PublishedBy` ve `WrittenBy`. İlişki `PublishedBy` ilişkilendirme için sonlanır `Book` ve `Publisher` varlık türleridir. `Publisher` ucunun çoğulluğu bir (1) ve `Book` ucunun çoğulluğu birçok (\*) ve bir yayımcının çok sayıda kitabı yayımladığını ve bir yayımcının bir yayımcı tarafından yayımlandığını belirtir.  
  
 ![Üç varlık türüne sahip örnek model](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen `PublishedBy` ilişkilendirmesini tanımlar:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
