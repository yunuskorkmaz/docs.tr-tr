---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786936"
---
# <a name="association-set-end"></a>association set end
*İlişki kümesi sonu* , [varlık türünü](entity-type.md) ve bir [ilişki kümesinin](association-set.md)sonunda [ayarlanan varlığı](entity-set.md) tanımlar. İlişki kümesi uçları bir ilişki kümesinin parçası olarak tanımlanır; bir ilişki kümesi, tam olarak iki ilişkilendirme kümesine sahip olmalıdır.  
  
 Bir ilişki kümesi bitiş tanımı aşağıdaki bilgileri içerir:  
  
- İlişki kümesine dahil olan varlık türlerinden biri. Istenir  
  
- İlişki kümesine dahil edilen varlık türü için ayarlanan varlık. Istenir  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `WrittenBy` ve. `PublishedBy`  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Aşağıdaki diyagramda, yukarıda gösterilen kavramsal modele bağlı`PublishedBy`olarak bir ilişki kümesi ()`Books` ve `Publishers`iki varlık kümesi (ve) gösterilmektedir. İlişki kümesi sonlanır `Books` ve `Publishers` varlık kümeleridir. Varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder. `Books` Benzer şekilde, PJ `Publisher` `Publishers` varlık kümesindeki bir örneği temsil eder. Bipj, `PublishedBy` `PublishedBy` ilişki kümesindeki ilişkilendirmenin bir örneğini temsil eder.  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal modelleri tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir DSL kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar. İlişki kümesi uçlarının her ilişkilendirme kümesi tanımının bir parçası olarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
