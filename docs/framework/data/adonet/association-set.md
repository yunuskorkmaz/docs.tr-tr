---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: af9297d9c827b12ed8611e99930234511f7f661c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204490"
---
# <a name="association-set"></a>association set
Bir *ilişki kümesi* için mantıksal bir kapsayıcıdır [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) örnekleri aynı türde. Bir ilişki kümesi, bir veri yapısı modelleme değil; diğer bir deyişle, veriler veya ilişkileri yapısını açıklamaz. Böylece bir veri deposuna eşlenebilir bunun yerine, bir ilişki kümesi bir yapısı (örneğin, ortak dil çalışma zamanı veya bir SQL Server veritabanı) barındıran veya depolama ortamı için Grup ilişkilendirme örnekleri için sağlar.  
  
 Bir ilişki kümesi içinde tanımlanan bir [varlık kapsayıcısı](../../../../docs/framework/data/adonet/entity-container.md), mantıksal bir gruplandırması olan [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md) ve ilişki Setleri.  
  
 Bir ilişki kümesi için bir tanım, aşağıdaki bilgileri içerir:  
  
-   İlişkilendirmenin adını ayarlayın. (Gerekli)  
  
-   Hangi örnekleri içerecek ilişkilendirme. (Gerekli)  
  
-   İki [ilişkilendirme ucu ayarlanmış](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `PublishedBy`, ve `WrittenBy`. İlişki Setleri hakkında bilgi diyagramda ilettiği değil olsa da, bir sonraki diyagramda bu modeli temelinde varlık setleri ve ilişki Setleri bir örnek gösterir.  
  
 ![Üç varlık türleri ile örnek modeli](./media/association-set/example-model-three-entity-types.gif)  
  
 Aşağıdaki örnek, bir ilişki kümesi gösterir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre. İçinde BI `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü. Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi. BiPj örneğini temsil eder `PublishedBy` ilişkilendirmeyi `PublishedBy` ilişki kümesi.  
  
 ![Kümeleri örnek gösteren ekran görüntüsü.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL, yukarıdaki diyagramda her bir ilişkilendirme için bir ilişki ile varlık kapsayıcısı tanımlar. Adı ve her bir ilişkilendirme ilişkisi Not XML öznitelikleri kullanılarak tanımlanır.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Bu ilişki, iki ilişkilendirme kümelerinin paylaşım uzun başına birden çok ilişki kümesi tanımlamak mümkündür bir [ilişkilendirme ayarlanmış son](../../../../docs/framework/data/adonet/association-set-end.md). Varlık kapsayıcısı için iki ilişki Setleri ile aşağıdaki CSDL tanımlar `WrittenBy` ilişkilendirme. Birden çok varlık kümesi için tanımlanmış bildirim `Book` ve `Author` varlık türleri ve hiçbir ilişki paylaşımları ilişkilendirme kümesi uç ayarlayın.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
- [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md)
