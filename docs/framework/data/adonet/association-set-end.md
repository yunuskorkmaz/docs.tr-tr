---
title: İlişki sonu Ayarla
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 9a71fd434bea87a75e259a3d5caa902fbecf8a57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701644"
---
# <a name="association-set-end"></a>İlişki sonu Ayarla
Bir *ilişkilendirme ayarlanmış son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişki kümesi](../../../../docs/framework/data/adonet/association-set.md). İlişki kümesi uçlarının bir ilişkilendirme kümesinin bir parçası tanımlanır; bir ilişki kümesi tam olarak iki ilişki kümesi uçlarının olması gerekir.  
  
 Bir ilişkilendirme kümesi son tanımı, şu bilgileri içerir:  
  
-   İlişkilendirmesine katılan varlık türlerinden birini ayarlayın. (Gerekli)  
  
-   Varlık için varlık türü ilişkilendirme kümesine katılan kümesi. (Gerekli)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `WrittenBy` ve `PublishedBy`.  
  
 ![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Aşağıdaki diyagramda bir ilişki kümesi gösterilmektedir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre. İlişki kümesi uçlarının olan `Books` ve `Publishers` varlık kümesi. İçinde BI `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü. Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi. BiPj örneğini temsil eder `PublishedBy` ilişkilendirmeyi `PublishedBy` ilişki kümesi.  
  
 ![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL, yukarıdaki diyagramda her bir ilişkilendirme için bir ilişki ile varlık kapsayıcısı tanımlar. İlişki kümesi uçlarının her ilişki kümesi tanımının bir parçası tanımlandığına dikkat edin.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
