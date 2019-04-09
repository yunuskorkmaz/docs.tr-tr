---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 7b6c646592c1878ea30396d98b4976dc8fa0be12
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134634"
---
# <a name="association-set-end"></a>association set end
Bir *ilişkilendirme ayarlanmış son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişki kümesi](../../../../docs/framework/data/adonet/association-set.md). İlişki kümesi uçlarının bir ilişkilendirme kümesinin bir parçası tanımlanır; bir ilişki kümesi tam olarak iki ilişki kümesi uçlarının olması gerekir.  
  
 Bir ilişkilendirme kümesi son tanımı, şu bilgileri içerir:  
  
-   İlişkilendirmesine katılan varlık türlerinden birini ayarlayın. (Gerekli)  
  
-   Varlık için varlık türü ilişkilendirme kümesine katılan kümesi. (Gerekli)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `WrittenBy` ve `PublishedBy`.  
  
 ![Üç varlık türleri ile örnek modeli](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Aşağıdaki diyagramda bir ilişki kümesi gösterilmektedir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre. İlişki kümesi uçlarının olan `Books` ve `Publishers` varlık kümesi. İçinde BI `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü. Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi. BiPj örneğini temsil eder `PublishedBy` ilişkilendirmeyi `PublishedBy` ilişki kümesi.  
  
 ![Kümeleri örnek gösteren ekran görüntüsü.](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL, yukarıdaki diyagramda her bir ilişkilendirme için bir ilişki ile varlık kapsayıcısı tanımlar. İlişki kümesi uçlarının her ilişki kümesi tanımının bir parçası tanımlandığına dikkat edin.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
