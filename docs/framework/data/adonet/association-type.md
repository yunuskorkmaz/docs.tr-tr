---
title: ilişki türü
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 7a16b4447c9ba35f1a81a8ff837abd984985b097
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="association-type"></a>ilişki türü
Bir *ilişkilendirme türü* (bir ilişki olarak da bilinir) ilişkileri varlık veri modeli (EDM) açıklamak için temel yapı bloğu. Bir kavramsal modelde ilişkilendirme iki arasındaki bir ilişkiyi temsil eder. [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) (gibi `Customer` ve `Order`). Bir uygulamada belirli bir ilişki ilişkilendirme örneğini temsil eder (bir örneği arasında bir ilişki gibi `Customer` bir örneği ile `Order`). İlişkilendirme örnekleri mantıksal olarak gruplandırılmış bir [ilişkilendirme kümesi](../../../../docs/framework/data/adonet/association-set.md).  
  
 Bir ilişkilendirme tanımı aşağıdaki bilgileri içerir:  
  
-   Benzersiz bir ad. (Gerekli)  
  
-   İki [ilişki uçları](../../../../docs/framework/data/adonet/association-end.md), ilişkiyi her bir varlık türü için bir tane. (Gerekli)  
  
    > [!NOTE]
    >  Bir ilişkilendirme ikiden fazla varlık türleri arasındaki ilişkiyi temsil edilemez. Bir ilişkilendirme ancak, kendi kendine ilişki her ilişki uçlarından biri için aynı varlık türü belirterek tanımlayabilirsiniz.  
  
-   A [başvuru bütünlüğü kısıtlaması](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (İsteğe bağlı)  
  
 Her ilişki ucu belirtmelisiniz bir [ilişkilendirme son Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) bir ilişki sonunda olabilir varlık türü örneklerinin sayısını belirtir. Bir ilişkilendirme end Çokluk bir değer (0.. 1 çokluğa) bir (1), sıfır veya bir veya birçok (*) olabilir. Varlık türü örnekleri ilişkinin bir ucundaki üzerinden erişilebilir [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) veya bir varlık türü gösteriliyorsa yabancı anahtarlar. Daha fazla bilgi için bkz: [varlık veri modeli: yabancı anahtarlar](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (*), bir yayımcı birçok books yayımlar ve kitap bir yayımcı tarafından yayımlanan gösteren.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
