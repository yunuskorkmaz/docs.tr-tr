---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934517"
---
# <a name="model-defined-function"></a>model-defined function
*Model tanımlı bir işlev* , kavramsal modelde tanımlanan bir işlevdir. Model tanımlı bir işlevin gövdesi [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)ifade edilir ve bu, işlevin veri kaynağında desteklenen kurallardan veya dillerden bağımsız olarak ifade etmesine olanak tanır.  
  
 Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:  
  
- Bir işlev adı. Istenir  
  
- Dönüş değerinin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    > Dönüş türü belirtilmemişse, dönüş değeri void olur.  
  
- Parametre bilgileri. (İsteğe bağlı)  
  
- İşlevin gövdesini tanımlayan bir [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) ifadesi.  
  
 Model tanımlı işlevlerin çıkış parametrelerini desteklemediğini unutmayın. Bu kısıtlama, model tanımlı işlevlerin birleştirilebilmesi için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book`, `Publisher`, ve `Author`.  
  
 ![Yayımlanma tarihi olan bir modeli gösteren ekran görüntüsü.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl, bir (Yukarıdaki diyagramda) bir `Book` örneği yayımlandığı için yıl sayılarını döndüren kavramsal modelde bir işlevi tanımlar.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Varlık Veri Modeli: İlkel veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
