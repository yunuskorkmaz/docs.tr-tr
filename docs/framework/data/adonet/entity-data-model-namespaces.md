---
title: 'Varlık veri modeli: Ad Alanları'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: aa11902ece5197905c20e7e572562643c57f51c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590113"
---
# <a name="entity-data-model-namespaces"></a>Varlık veri modeli: Ad Alanları
Ad alanı varlık veri modeli (EDM) soyut bir kapsayıcıdır [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md), [karmaşık türler](../../../../docs/framework/data/adonet/complex-type.md), ve [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md). EDM ad alanları, ad alanları bir programlama dilinde benzerdir: içerdikleri nesneleri bağlam sağlarlar ve aynı ada sahip (ancak farklı ad alanlarına yer) nesneleri ayırt etmek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL kod, farklı bir kavramsal modelde tanımlı bir tür tanımlamak için bir ad alanı kullanır. Örnek, bir varlık türü tanımlar. (`Publisher`) olan bir karmaşık tür özelliği (`Address`) öğesinden alınan `ExtendedBooksModel` ad alanı. Unutmayın `Using` öğeyi gösteren bir ad alanı içeri aktarıldı. Ayrıca türünü `Address` özelliği, tam adı kullanılarak tanımlanır (`ExtendedBooksModel.Address`), bu tür tanımlanan belirten `ExtendedBooksModel` ad alanı.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
