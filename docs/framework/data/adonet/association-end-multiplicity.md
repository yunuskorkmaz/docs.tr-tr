---
title: "İlişki uç Çokluk"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d66c141b83402b011fdebbb04c0b2a9adc5ec29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="association-end-multiplicity"></a>İlişki uç Çokluk
*İlişki uç Çokluk* sayısını tanımlar [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir sonunda olabilir örnekleri bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md).  
  
 Bir ilişkilendirme end Çokluk şu değerlerden biri olabilir:  
  
-   bir (1): Bu tam olarak bir varlık türü örneği var ilişkisi sonunda gösterir.  
  
-   sıfır veya bir (0.. 1 çokluğa): sıfır veya bir varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.  
  
-   birçok (*): sıfır, bir veya daha fazla varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.  
  
 Bir ilişkilendirme genellikle kendi ilişkilendirme son Çeşitlilikler tarafından belirlenir. Örneğin, bir ilişki uçlarından biri (1) ve çok sayıda Çeşitlilikler (*) varsa, ilişki bir-çok ilişkisi adı verilir. Aşağıdaki örnekte `PublishedBy` ilişkilendirmedir bir-çok ilişkisi (birçok books yayımcı yayımlar ve kitap bir yayımcı tarafından yayımlanan). `WrittenBy` İlişkilendirmedir bir çok-çok ilişkisi (kitap birden çok yazar olabilir ve bir yazar birden çok books yazabilirsiniz).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (*).  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) ADO.NET Entity Framework kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
