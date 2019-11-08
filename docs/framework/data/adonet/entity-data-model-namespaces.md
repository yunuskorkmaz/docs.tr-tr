---
title: 'Varlık Veri Modeli: ad alanları'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a403bcd459005ed9cea4a455fcde40c31c8caac9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738435"
---
# <a name="entity-data-model-namespaces"></a>Varlık Veri Modeli: ad alanları
Varlık Veri Modeli (EDM) içindeki bir ad alanı, [varlık türleri](entity-type.md), [karmaşık türler](complex-type.md)ve [ilişkilendirmeler](association-type.md)için soyut bir kapsayıcıdır. EDM 'daki ad alanları, bir programlama dilinde ad alanlarına benzerdir: içerdikleri nesneler için bağlam sağlar ve aynı ada sahip nesneleri belirsizliğini (ancak farklı ad alanlarında bulunan) ayırt etmek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL kodu, farklı bir kavramsal modelde tanımlanan bir türü tanımlamak için bir ad alanı kullanır. Örnek, `ExtendedBooksModel` ad alanından içeri aktarılan karmaşık tür özelliğine (`Address`) sahip bir varlık türü (`Publisher`) tanımlar. `Using` öğesinin, bir ad alanının içeri aktarıldığını olduğunu unutmayın. Ayrıca, `Address` özelliğinin türünün, bu türün `ExtendedBooksModel` ad alanında tanımlandığını belirten tam adı (`ExtendedBooksModel.Address`) kullanılarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
