---
title: "Varlık kümesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 050c73d3fd9146c8eee83baf1bd504acc18c8718
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-set"></a>Varlık kümesi
Bir *varlık kümesini* için mantıksal bir kapsayıcısıdır örnekleri bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve örnekleri bu varlık türünden türetilmiş herhangi bir türde. (Türetilmiş türler hakkında daha fazla bilgi için bkz: [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Bir satır ve ilişkisel bir veritabanındaki bir tablo arasındaki ilişki için bir varlık türünün varlık kümesi arasındaki ilişkiyi benzerdir: bir satır gibi bir varlık türü veri yapısını açıklar ve bir tablo gibi bir varlık kümesini verilen bir yapının örneklerini içerir. Bir varlık kümesini yapı modelleme veri değil; verilerin yapısını açıklamaz. Böylece bir veri deposuna eşlenen bunun yerine, bir varlık kümesini bir yapı (örneğin, ortak dil çalışma zamanı veya SQL Server veritabanı) barındıran veya depolama bir ortam için Grup varlık türü örnekleri sağlar.  
  
 Bir varlık kümesi içinde tanımlanan bir [varlık kapsayıcısının](../../../../docs/framework/data/adonet/entity-container.md), varlık kümeleri mantıksal bir gruplandırması olan ve [ilişki kümeleri](../../../../docs/framework/data/adonet/association-set.md).  
  
 Bir varlık kümesinde var varlık türü için bir örneği, aşağıdakilerin doğru olması gerekir:  
  
-   Örnek türü ya da'varlık kümesi tabanlı veya örnek varlık türünün bir alt türünde varlık türü olarak aynıdır.  
  
-   [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) için varlık kümesi içinde benzersiz bir örneğidir.  
  
-   Örneği başka bir varlık kümesinde yok.  
  
    > [!NOTE]
    >  Birden çok varlık kümesine aynı varlık türü kullanılarak tanımlanabilir, ancak belirtilen varlık türünün bir örneği yalnızca tek bir varlık kümesinde var olabilir.  
  
 Bir varlık için kavramsal modeldeki her bir varlık türü kümesine tanımlamak zorunda değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Aşağıdaki diyagramda iki varlık kümelerini gösterir (`Books` ve `Publishers`) ve bir ilişkilendirme kümesine (`PublishedBy`) yukarıda gösterilen kavramsal model göre. İçinde bi `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü. Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi. BiPj örneğini temsil eder `PublishedBy` ilişkilendirme `PublishedBy` ilişkilendirme kümesi.  
  
 ![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL yukarıda gösterilen kavramsal modeldeki her bir varlık türü için ayarlanmış bir varlığı olan bir varlık kapsayıcı tanımlar. Her varlık kümesi için ad ve varlık türü Not XML özniteliği kullanılarak tanımlanır.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Tür (MEST) başına birden çok varlık kümesine tanımlamak mümkündür. Bir varlık kapsayıcısı için iki varlık kümeleri ile aşağıdaki CSDL tanımlar `Book` varlık türü:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
