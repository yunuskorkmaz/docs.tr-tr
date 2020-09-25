---
title: 'Varlık Veri Modeli: Ad Alanları'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 1e5f9527ec208c5650c68fe35bb758e0850b7700
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194836"
---
# <a name="entity-data-model-namespaces"></a>Varlık Veri Modeli: Ad Alanları

Varlık Veri Modeli (EDM) içindeki bir ad alanı, [varlık türleri](entity-type.md), [karmaşık türler](complex-type.md)ve [ilişkilendirmeler](association-type.md)için soyut bir kapsayıcıdır. EDM 'daki ad alanları, bir programlama dilinde ad alanlarına benzerdir: içerdikleri nesneler için bağlam sağlar ve aynı ada sahip nesneleri belirsizliğini (ancak farklı ad alanlarında bulunan) ayırt etmek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  

 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL kodu, farklı bir kavramsal modelde tanımlanan bir türü tanımlamak için bir ad alanı kullanır. Örnek, `Publisher` `Address` ad alanından içeri aktarılan karmaşık tür özelliğine () sahip bir varlık türü () tanımlar `ExtendedBooksModel` . `Using`Öğesinin bir ad alanının içeri aktarıldığını olduğunu unutmayın. Ayrıca, özelliğin türünün, `Address` `ExtendedBooksModel.Address` Bu türün ad alanında tanımlandığını belirten tam adı () kullanılarak tanımlandığını unutmayın `ExtendedBooksModel` .  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
