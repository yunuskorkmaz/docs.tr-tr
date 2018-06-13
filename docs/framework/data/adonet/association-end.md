---
title: ilişki ucu
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 9d7bd6fa92a4337add18deafbeb5ad28fefcb749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757443"
---
# <a name="association-end"></a>ilişki ucu
Bir *ilişki ucu* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir ucunda bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) ve varlık sayısı bu ilişkilendirmeyi sonunda bulunabilir örnekleri yazın. İlişki Uçları ilişkilendirme bir parçası olarak tanımlanan; bir ilişkilendirme tam olarak iki ilişki ucu olması gerekir. [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) diğer gezinti bölmesinden bir ilişki ucu izin verir.  
  
 Bir ilişkilendirme end tanımı aşağıdaki bilgileri içerir:  
  
-   İlişkide ilgili varlık türleri biri. (Gerekli)  
  
    > [!NOTE]
    >  Belirli bir ilişkilendirme için her ilişki ucu için belirtilen varlık türü aynı olabilir. Bu, kendi kendine bir ilişki oluşturur.  
  
-   Bir [ilişkilendirme son Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) bir ilişki sonunda olabilir varlık türü örneklerinin sayısını belirtir. Bir ilişkilendirme end Çokluk bir değer (0.. 1 çokluğa) bir (1), sıfır veya bir veya birçok (*) olabilir.  
  
-   İlişki ucu için bir ad. (İsteğe bağlı)  
  
-   Cascade delete üzerinde gibi ilişki ucu üzerinde gerçekleştirilen işlemler hakkında bilgi. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (*), bir yayımcı birçok books yayımlar ve kitap bir yayımcı tarafından yayımlanan gösteren.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) ADO.NET Entity Framework kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme. Türü, adı ve her ilişkilendirme ucunun çokluğu XML özniteliği tarafından belirtilen unutmayın ( `Type`, `Role`, ve `Multiplicity` öznitelikleri, sırasıyla). Bir tarafta gerçekleştirilen işlemler hakkında isteğe bağlı bilgileri bir XML öğesi belirtilen ( `OnDelete` öğesi). Bu durumda, bir yayımcı silinir, böylece tüm ilişkili books demektir.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
