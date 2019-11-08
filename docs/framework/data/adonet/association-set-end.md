---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: f7ec1ca6fcdf299b9fcfc78f299ea4c6c5267cd3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738622"
---
# <a name="association-set-end"></a>association set end
*İlişki kümesi sonu* , [varlık türünü](entity-type.md) ve bir [ilişki kümesinin](association-set.md)sonunda [ayarlanan varlığı](entity-set.md) tanımlar. İlişki kümesi uçları bir ilişki kümesinin parçası olarak tanımlanır; bir ilişki kümesi, tam olarak iki ilişkilendirme kümesine sahip olmalıdır.  
  
 Bir ilişki kümesi bitiş tanımı aşağıdaki bilgileri içerir:  
  
- İlişki kümesine dahil olan varlık türlerinden biri. Istenir  
  
- İlişki kümesine dahil edilen varlık türü için ayarlanan varlık. Istenir  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip bir kavramsal model görülmektedir: `WrittenBy` ve `PublishedBy`.  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Aşağıdaki diyagramda, yukarıda gösterilen kavramsal modele bağlı olarak bir ilişki kümesi (`PublishedBy`) ve iki varlık kümesi (`Books` ve `Publishers`) gösterilmektedir. İlişki kümesi sona erer `Books` ve `Publishers` varlık kümeleridir. `Books` varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder. Benzer şekilde, PJ, `Publishers` varlık kümesindeki bir `Publisher` örneğini temsil eder. BiPj, `PublishedBy` ilişkilendirme kümesindeki `PublishedBy` ilişkisinin bir örneğini temsil eder.  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal modelleri tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir DSL kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar. İlişki kümesi uçlarının her ilişkilendirme kümesi tanımının bir parçası olarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
