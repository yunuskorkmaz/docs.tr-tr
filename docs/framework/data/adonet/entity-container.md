---
title: "Varlık kapsayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5ac4383e68aad49af1a65988d9993f6fa018b31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-container"></a>Varlık kapsayıcısı
Bir *varlık kapsayıcısının* mantıksal bir gruplandırmasıdır [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md), [ilişki kümeleri](../../../../docs/framework/data/adonet/association-set.md), ve [işlev içeri aktarmalar](../../../../docs/framework/data/adonet/model-declared-function.md).  
  
 Aşağıdaki kavramsal modelde tanımlanan bir varlık kapsayıcısının true olması gerekir:  
  
-   En az bir varlık kapsayıcısının her kavramsal modelde tanımlanmış olması gerekir.  
  
-   Varlık kapsayıcısının her kavramsal model içinde benzersiz bir adı olması gerekir.  
  
 Bir varlık kapsayıcısı varlık kümesi veya varlık türleri veya bir veya daha fazla ad içinde tanımlanan ilişkileri kullanan ilişkilendirme kümeleri tanımlayabilirsiniz. Daha fazla bilgi için bkz: [varlık veri modeli: ad alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.  Sonraki örnek daha fazla bilgi için bkz.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Diyagram varlık kapsayıcı bilgileri iletmek değil de, kavramsal modele bir varlık kapsayıcısı tanımlamanız gerekir. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL Yukarıdaki diyagramda gösterildiği kavramsal model için bir varlık kapsayıcı tanımlar. Kapsayıcı adı bir XML özniteliği tanımlanır unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık veri modeli temel kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
