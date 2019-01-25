---
title: ilişki türü
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 3b01e053a1d61e2ce413ae6683d350b77c402fb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714600"
---
# <a name="association-type"></a>ilişki türü
Bir *ilişkilendirme türü* (ilişkilendirme olarak da bilinir) ilişkilerini varlık veri modeli (EDM) tanımlamak için temel yapı taşı. Bir kavramsal modelde, ikisi arasında bir ilişki bir ilişkiyi temsil eder [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) (gibi `Customer` ve `Order`). Bir uygulamada belirli bir ilişki bir ilişki örneğini temsil eder (örneği arasında bir ilişki gibi `Customer` ve örneği `Order`). İlişkilendirme örnekleri mantıksal olarak gruplandırılır bir [ilişki kümesi](../../../../docs/framework/data/adonet/association-set.md).  
  
 Bir ilişki tanımı aşağıdaki bilgileri içerir:  
  
-   Benzersiz bir ad. (Gerekli)  
  
-   İki [ilişkilendirme ucu](../../../../docs/framework/data/adonet/association-end.md), bir ilişkideki her varlık türü. (Gerekli)  
  
    > [!NOTE]
    >  Bir ilişkilendirme ikiden fazla varlık türleri arasındaki ilişkiyi temsil edemez. Bir ilişkilendirme ancak kendi kendine ilişki her ilişki uçlarından biri için aynı varlık değerlerini belirterek tanımlayabilirsiniz.  
  
-   A [başvuru bütünlüğü kısıtlaması](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (İsteğe bağlı)  
  
 Her bir ilişkilendirme end belirtmelisiniz bir [ilişkilendirme end çoğulluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) ilişkilendirme sonunda olabilir bir varlık türü örneklerinin sayısını belirtir. Bir ilişkilendirme end çoğulluk değeri (0..1) bir (1) sıfır veya bir veya birçok (*) olabilir. Varlık türü örneklerinin bir ilişkilendirmenin bir ucunda, üzerinden erişilebilir [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) veya bir varlık türünde gösteriliyorsa yabancı anahtarlar. Daha fazla bilgi için [varlık veri modeli: Yabancı anahtarlar](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona için `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çeşitliliğini `Book` sonudur birçok (*), bir yayımcı bir çok kitap yayımlar ve bir yayımcı tarafından yayımlanan bir kitap gösteren.  
  
 ![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkiyi:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
