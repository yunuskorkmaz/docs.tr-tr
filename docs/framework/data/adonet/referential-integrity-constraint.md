---
title: "başvuru bütünlüğü kısıtlaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 232098a4940e223fd8553eefa4964777b1695c5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="referential-integrity-constraint"></a>başvuru bütünlüğü kısıtlaması
A *başvuru bütünlüğü kısıtlaması* varlık veri modeli (EDM) ilişkisel bir veritabanındaki bir başvuru bütünlüğü kısıtlaması benzer. Bir veritabanı tablodaki bir sütuna (veya sütun) başka bir tablonun birincil anahtarı başvurabilir aynı şekilde bir [özelliği](../../../../docs/framework/data/adonet/property.md) (veya Özellikler), bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) başvurabilir [Varlık anahtarı ](../../../../docs/framework/data/adonet/entity-key.md) başka bir varlık türü. Başvurulan varlık türü olarak adlandırılan *asıl ucu* kısıtlaması. Asıl ucu başvuruda bulunan varlık türü olarak adlandırılan *bağımlı uç* kısıtlaması.  
  
 Bir başvuru bütünlüğü kısıtlamasının bir parçası olarak tanımlanan bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) iki varlık türleri arasındaki. Tanımı bir başvuru bütünlüğü kısıtlaması için aşağıdaki bilgileri belirtir:  
  
-   Kısıtlamasının asıl uç. (Yalnızca Varlık anahtarı bağımlı uç tarafından başvurulan bir varlık türü.)  
  
-   Asıl ucu Varlık anahtarı.  
  
-   Kısıtlamasının bağımlı uç. (Bir özellik veya asıl ucu Varlık anahtarı başvuran özellikleri olan bir varlık türü.)  
  
-   Başvuruda bulunan özellik veya bağımlı uç özellikleri.  
  
 EDM başvuru bütünlüğü kısıtlamalarını amacı geçerli ilişkilendirmeleri her zaman var olduğundan emin olmaktır. Daha fazla bilgi için bkz: [yabancı anahtar özelliği](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `WrittenBy` ve `PublishedBy`. `Book` Varlık türüne sahip bir özellik `PublisherId`, varlık anahtarı başvuran `Publisher` bir başvuru bütünlüğü kısıtlaması tanımlarken varlık türü `PublishedBy` ilişkilendirme.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL üzerindeki bir başvuru bütünlüğü kısıtlaması tanımlar `PublishedBy` yukarıdaki kavramsal modelde gösterilen ilişkilendirme.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
