---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 77152e8f37b009cbc3e72f053ead867914768d3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772267"
---
# <a name="model-defined-function"></a>model-defined function
A *model tanımlı işlev* kavramsal modelde tanımlı bir işlev değil. Model tanımlı bir işlev gövdesini gösterdiğini [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), işlevin bağımsız ifade sağlayan kuralları veya veri kaynağındaki desteklenen diller.  
  
 Bir model tanımlı işlev tanımı, şu bilgileri içerir:  
  
- Bir işlev adı. (Gerekli)  
  
- Dönüş değerinin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    >  Dönüş değeri, dönüş türü belirtilirse, geçersizdir.  
  
- Parametre bilgileri. (İsteğe bağlı)  
  
- Bir [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) işlevinin gövdesi tanımlayan ifade.  
  
 Not model tanımlı işlevleri çıkış parametreleri desteklemez. Böylece model tanımlı işlevleri oluşan bu kısıtlama yerdir.  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.  
  
 ![Yayımlanma tarihi modeliyle gösteren ekran görüntüsü.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL örneği itibaren bir yıl sayılarını döndüren kavramsal modeldeki bir işlevi tanımlayan bir `Book` (Yukarıdaki diyagramda) olarak yayımlandı.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Varlık veri modeli: Basit veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
