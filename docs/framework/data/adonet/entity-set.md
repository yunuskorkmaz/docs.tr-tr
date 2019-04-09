---
title: entity set
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 7fcaa2cb9bac02271940a712d4d044df25d7d4cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126626"
---
# <a name="entity-set"></a>entity set
Bir *varlık kümesi* için mantıksal bir kapsayıcıdır örneklerini bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve bu varlık türünden türetilmiş herhangi bir tür örneği. (Türetilen türleri hakkında daha fazla bilgi için bkz. [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Bir varlık türü ve bir varlık kümesi arasındaki ilişki, satır ve ilişkisel bir veritabanındaki bir tablo arasındaki ilişkiyi benzerdir: Bir satır gibi bir varlık türü, veri yapısını açıklar ve bir tablo gibi belirli bir yapının örneği bir varlık kümesini içerir. Bir varlık kümesindeki bir veri yapısı modelleme değil; verilerin yapısını açıklamaz. Bir veri deposuna eşlenebilir bunun yerine, bir varlık kümesindeki bir yapısı (örneğin, ortak dil çalışma zamanı veya bir SQL Server veritabanı) barındıran veya depolama ortamı için Grup varlık türü örneklerine sağlar.  
  
 Bir varlık kümesi içinde tanımlanan bir [varlık kapsayıcısı](../../../../docs/framework/data/adonet/entity-container.md), varlık kümelerini mantıksal bir gruplandırması olan ve [ilişki Setleri](../../../../docs/framework/data/adonet/association-set.md).  
  
 Bir varlık kümesinde var varlık türü için bir örneği, aşağıdakilerin doğru olması gerekir:  
  
-   Örnek türünün ya da'varlık kümesini alır veya varlık türünün bir alt türdür örneğinin varlık türü olarak aynıdır.  
  
-   [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) için varlık kümesi içinde benzersiz bir örneğidir.  
  
-   Örneği başka bir varlık kümesinde yok.  
  
    > [!NOTE]
    >  Birden çok varlık kümeleri aynı varlık türü kullanarak tanımlanabilir, ancak belirtilen varlık türünün bir örneği yalnızca bir varlık kümesinde var olabilir.  
  
 Kavramsal modelde her varlık türü için bir varlık tanımlamak zorunda değildir.  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.  
  
 ![Üç varlık türleri ile örnek modeli](./media/entity-set/example-model-three-entity-types.gif)  
  
 Aşağıdaki diyagramda iki varlık kümelerini gösterir (`Books` ve `Publishers`) ve ilişkilendirme ayarlayın (`PublishedBy`) yukarıda gösterilen kavramsal model göre. İçinde BI `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü. Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi. BiPj örneğini temsil eder `PublishedBy` ilişkilendirmeyi `PublishedBy` ilişki kümesi.  
  
 ![Kümeleri örnek gösteren ekran görüntüsü.](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL, yukarıda gösterilen kavramsal modeldeki her bir varlık türü için bir varlık ile varlık kapsayıcısı tanımlar. Her varlık kümesi için ad ve varlık türü Not, XML öznitelikleri kullanılarak tanımlanır.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Tür (MEST) başına birden çok varlık kümesi tanımlamak mümkündür. Varlık kapsayıcısı için iki varlık kümeleri aşağıdaki CSDL tanımlar `Book` varlık türü:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
