---
title: "ilişkilendirme kümesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa977f69951184629f4e9555f524f074a09ce96a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="association-set"></a>ilişkilendirme kümesi
Bir *ilişkilendirme kümesi* için mantıksal bir kapsayıcısıdır [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) örnekleri aynı türde. Bir ilişkilendirme kümesi yapı modelleme veri değil; diğer bir deyişle, verileri veya ilişkileri yapısını açıklamaz. Böylece bir veri deposuna eşlenen bunun yerine, bir ilişkilendirme kümesine bir yapı için (örneğin, ortak dil çalışma zamanı veya SQL Server veritabanı) barındıran veya depolama bir ortam grubu ilişkisi örneklerine sağlar.  
  
 Bir ilişkilendirme kümesi içinde tanımlanan bir [varlık kapsayıcısının](../../../../docs/framework/data/adonet/entity-container.md), mantıksal bir gruplandırması olan [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md) ve ilişki kümeleri.  
  
 Bir ilişkilendirme kümesi için bir tanım aşağıdaki bilgileri içerir:  
  
-   İlişki kümesi adı. (Gerekli)  
  
-   Hangi örnekleri içerecek ilişki. (Gerekli)  
  
-   İki [ilişki uçları kümesi](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy`, ve `WrittenBy`. İlişki kümeleri hakkında bilgi diyagramda ilettiği değil de, sonraki diyagramda ilişkilendirme ayarlar ve bu modelini temel varlık kümeleri örneği gösterilmektedir.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Aşağıdaki örnek, bir ilişkilendirme kümesine gösterir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre. İçinde bi `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü. Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi. BiPj örneğini temsil eder `PublishedBy` ilişkilendirme `PublishedBy` ilişkilendirme kümesi.  
  
 ![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL bir ilişkilendirme için yukarıdaki diyagramdaki her bir ilişkilendirme kümesine sahip bir varlık kapsayıcı tanımlar. Her bir ilişkilendirme için ilişkilendirme ve adını ayarlayın Not XML öznitelikleri kullanılarak tanımlanır.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Association, hiçbir iki ilişki kümeleri paylaşımı olarak uzunluğunda başına birden çok ilişkilendirme kümesi tanımlamak mümkündür bir [ilişkilendirme kümesi son](../../../../docs/framework/data/adonet/association-set-end.md). Bir varlık kapsayıcısı için iki ilişkilendirme kümeleriyle aşağıdaki CSDL tanımlar `WrittenBy` ilişkilendirme. Birden çok varlık kümesi için tanımlanmış bildirim `Book` ve `Author` varlık türleri ve ilişkisi olmayan bir ilişki paylaşımları kümesi son ayarlayın.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md)
