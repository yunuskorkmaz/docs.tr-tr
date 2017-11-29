---
title: "İlişki sonu Ayarla"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20810eddda98403d244f6104807504489dde71cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="association-set-end"></a>İlişki sonu Ayarla
Bir *ilişkilendirme kümesi son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesini](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişkilendirme kümesi](../../../../docs/framework/data/adonet/association-set.md). İlişkilendirme kümesi uçları bir ilişkilendirme kümesinin bir parçası tanımlanan; bir ilişkilendirme kümesine tam olarak iki ilişkilendirme kümesi uçları sahip olmalıdır.  
  
 Bir ilişkilendirme kümesi son tanımı aşağıdaki bilgileri içerir:  
  
-   Bir ilişkide ilgili varlık türlerinin ayarlayın. (Gerekli)  
  
-   Varlık için varlık türü ilişkilendirme kümesine dahil edilen kümesi. (Gerekli)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `WrittenBy` ve `PublishedBy`.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Aşağıdaki diyagramda bir ilişkilendirme kümesine gösterir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre. İlişkilendirme kümesi uçları olan `Books` ve `Publishers` varlık kümeleri. İçinde bi `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü. Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi. BiPj örneğini temsil eder `PublishedBy` ilişkilendirme `PublishedBy` ilişkilendirme kümesi.  
  
 ![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL bir ilişkilendirme için yukarıdaki diyagramdaki her bir ilişkilendirme kümesine sahip bir varlık kapsayıcı tanımlar. İlişkilendirme kümesi uçları her ilişkilendirme kümesi tanımının bir parçası tanımlanan unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık veri modeli temel kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
