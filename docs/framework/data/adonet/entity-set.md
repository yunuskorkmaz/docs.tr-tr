---
title: entity set
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a2465801c270813dd7bca2144d05fa202571153
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738428"
---
# <a name="entity-set"></a>entity set
*Varlık kümesi* , [varlık türü](entity-type.md) örnekleri ve bu varlık türünden türetilmiş herhangi bir türün örnekleri için mantıksal bir kapsayıcıdır. (Türetilmiş türler hakkında bilgi için bkz. [varlık veri modeli: devralma](entity-data-model-inheritance.md).) Bir varlık türü ve bir varlık kümesi arasındaki ilişki, bir satır ile ilişkisel veritabanındaki bir tablo arasındaki ilişkiye benzerdir: bir satır gibi, bir varlık türü veri yapısını tanımlar ve tablo gibi bir varlık kümesi, belirli bir yapının örneklerini içerir. Bir varlık kümesi, bir veri modelleme yapısı değildir; verilerin yapısını tanımlamaz. Bunun yerine, bir varlık kümesi, varlık türü örneklerinin bir veri deposuyla eşleştiribilecekleri şekilde gruplandırılması için bir barındırma veya depolama ortamı (ortak dil çalışma zamanı veya bir SQL Server veritabanı gibi) için bir yapı sağlar.  
  
 Varlık kümesi, varlık kümelerinin ve [ilişkilendirme kümelerinin](association-set.md)mantıksal bir gruplandırması olan bir [varlık kapsayıcısı](entity-container.md)içinde tanımlanır.  
  
 Bir varlık kümesinde bir varlık türü örneğinin mevcut olması için, aşağıdakilerin doğru olması gerekir:  
  
- Örneğin türü, varlık kümesinin temel aldığı varlık türü ile aynı veya örneğin türü varlık türünün bir alt türü.  
  
- Örnek için [varlık anahtarı](entity-key.md) varlık kümesi içinde benzersizdir.  
  
- Örnek başka bir varlık kümesinde yok.  
  
    > [!NOTE]
    > Birden çok varlık kümesi aynı varlık türü kullanılarak tanımlanabilir, ancak belirli bir varlık türünün bir örneği yalnızca bir varlık kümesinde bulunabilir.  
  
 Kavramsal modeldeki her varlık türü için bir varlık kümesi tanımlamanız gerekmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda üç varlık türü olan kavramsal bir model gösterilmektedir: `Book`, `Publisher`ve `Author`.  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-set/example-model-three-entity-types.gif)  
  
 Aşağıdaki diyagramda, yukarıda gösterilen kavramsal modele göre iki varlık kümesi (`Books` ve `Publishers`) ve bir ilişki kümesi (`PublishedBy`) gösterilmektedir. `Books` varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder. Benzer şekilde, PJ, `Publishers` varlık kümesindeki bir `Publisher` örneğini temsil eder. BiPj, `PublishedBy` ilişkilendirme kümesindeki `PublishedBy` ilişkisinin bir örneğini temsil eder.  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, yukarıda gösterilen kavramsal modeldeki her bir varlık türü için tek bir varlık kümesine sahip bir varlık kapsayıcısını tanımlar. Her bir varlık kümesi için ad ve varlık türünün XML öznitelikleri kullanılarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Tür başına birden çok varlık kümesi tanımlamak mümkündür (MEST). Aşağıdaki CSDL `Book` varlık türü için iki varlık kümesiyle bir varlık kapsayıcısını tanımlar:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
