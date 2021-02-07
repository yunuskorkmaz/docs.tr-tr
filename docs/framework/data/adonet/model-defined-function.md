---
description: 'Daha fazla bilgi edinin: model tanımlı işlev'
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 146ef4a8ad8c38897b8e56b6bc1485e1e40754cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723749"
---
# <a name="model-defined-function"></a>model-defined function

*Model tanımlı bir işlev* , kavramsal modelde tanımlanan bir işlevdir. Model tanımlı bir işlevin gövdesi [Entity SQL](./ef/language-reference/entity-sql-language.md)ifade edilir ve bu, işlevin veri kaynağında desteklenen kurallardan veya dillerden bağımsız olarak ifade etmesine olanak tanır.  
  
 Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:  
  
- İşlev adı. Istenir  
  
- Dönüş değerinin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    > Dönüş türü belirtilmemişse, dönüş değeri void olur.  
  
- Parametre bilgileri. (İsteğe bağlı)  
  
- İşlevin gövdesini tanımlayan bir [Entity SQL](./ef/language-reference/entity-sql-language.md) ifadesi.  
  
 Model tanımlı işlevlerin çıkış parametrelerini desteklemediğini unutmayın. Bu kısıtlama, model tanımlı işlevlerin birleştirilebilmesi için kullanılır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .  
  
 ![Yayımlanma tarihi olan bir modeli gösteren ekran görüntüsü.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, bir `Book` (Yukarıdaki diyagramda) bir örneği yayımlandığı için yıl sayılarını döndüren kavramsal modelde bir işlevi tanımlar.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
- [Varlık Veri Modeli: Basit Veri Türleri](entity-data-model-primitive-data-types.md)
