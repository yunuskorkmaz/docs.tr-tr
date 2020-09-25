---
title: entity set
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 6286d3707a8506e7a389359a5aa361c152e75212
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194803"
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

 Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-set/example-model-three-entity-types.gif)  
  
 Aşağıdaki diyagramda, `Books` `Publishers` `PublishedBy` yukarıda gösterilen kavramsal modeli temel alan iki varlık kümesi (ve) ve bir ilişki kümesi () gösterilmektedir. `Books`Varlık kümesindeki bı, `Book` çalışma zamanında varlık türünün bir örneğini temsil eder. Benzer şekilde, PJ `Publisher` varlık kümesindeki bir örneği temsil eder `Publishers` . BiPj `PublishedBy` , ilişki kümesindeki ilişkilendirmenin bir örneğini temsil eder `PublishedBy` .  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, yukarıda gösterilen kavramsal modeldeki her bir varlık türü için tek bir varlık kümesine sahip bir varlık kapsayıcısını tanımlar. Her bir varlık kümesi için ad ve varlık türünün XML öznitelikleri kullanılarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Tür başına birden çok varlık kümesi tanımlamak mümkündür (MEST). Aşağıdaki CSDL varlık türü için iki varlık kümesiyle bir varlık kapsayıcısını tanımlar `Book` :  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
