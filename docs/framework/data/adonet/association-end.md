---
title: "ilişki ucu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7ceb6d40a47c73c4580a8fc33acc3c395a2c5a06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="association-end"></a>ilişki ucu
Bir *ilişki ucu* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir ucunda bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) ve varlık sayısı bu ilişkilendirmeyi sonunda bulunabilir örnekleri yazın. İlişki Uçları ilişkilendirme bir parçası olarak tanımlanan; bir ilişkilendirme tam olarak iki ilişki ucu olması gerekir. [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) diğer gezinti bölmesinden bir ilişki ucu izin verir.  
  
 Bir ilişkilendirme end tanımı aşağıdaki bilgileri içerir:  
  
-   İlişkide ilgili varlık türleri biri. (Gerekli)  
  
    > [!NOTE]
    >  Belirli bir ilişkilendirme için her ilişki ucu için belirtilen varlık türü aynı olabilir. Bu, kendi kendine bir ilişki oluşturur.  
  
-   Bir [ilişkilendirme son Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) bir ilişki sonunda olabilir varlık türü örneklerinin sayısını belirtir. Bir ilişkilendirme end Çokluk bir değer (0.. 1 çokluğa) bir (1), sıfır veya bir veya birçok (*) olabilir.  
  
-   İlişki ucu için bir ad. (İsteğe bağlı)  
  
-   Cascade delete üzerinde gibi ilişki ucu üzerinde gerçekleştirilen işlemler hakkında bilgi. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (*), bir yayımcı birçok books yayımlar ve kitap bir yayımcı tarafından yayımlanan gösteren.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) ADO.NET Entity Framework kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme. Türü, adı ve her ilişkilendirme ucunun çokluğu XML özniteliği tarafından belirtilen unutmayın ( `Type`, `Role`, ve `Multiplicity` öznitelikleri, sırasıyla). Bir tarafta gerçekleştirilen işlemler hakkında isteğe bağlı bilgileri bir XML öğesi belirtilen ( `OnDelete` öğesi). Bu durumda, bir yayımcı silinir, böylece tüm ilişkili books demektir.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık veri modeli temel kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
