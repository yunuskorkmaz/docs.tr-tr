---
title: "Varlık veri modeli: ad alanları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e473453576f04e89b58806c5140e29855d7d022
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model-namespaces"></a>Varlık veri modeli: ad alanları
Varlık veri modeli (EDM) ad alanı için bir Özet kapsayıcıdır [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md), [karmaşık türler](../../../../docs/framework/data/adonet/complex-type.md), ve [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md). EDM ad alanları, ad alanları bir programlama dili benzerdir: içerirler nesneler için bağlamı ve aynı ada sahip (ancak farklı ad alanlarında bulunan) nesneleri belirsizliğini ortadan kaldırmak için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL kodu farklı bir kavramsal modelde tanımlanan bir türü tanımlamak için bir ad alanı kullanır. Örnek, bir varlık türünü tanımlar (`Publisher`), bir karmaşık tür özelliğe sahiptir (`Address`) öğesinden alınan `ExtendedBooksModel` ad alanı. Unutmayın `Using` öğesi gösteren bir ad alanı içeri aktarıldı. Ayrıca türünü `Address` özelliği, tam olarak nitelenmiş adını kullanarak tanımlanır (`ExtendedBooksModel.Address`), bu tür tanımlanan belirten `ExtendedBooksModel` ad alanı.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık veri modeli temel kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
