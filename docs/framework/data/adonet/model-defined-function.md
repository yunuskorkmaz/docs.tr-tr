---
title: Model tanımlı işlevi
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 371af3ae090e37cfd425a9e9d5946bb0751dc527
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538888"
---
# <a name="model-defined-function"></a>Model tanımlı işlevi
A *model tanımlı işlev* kavramsal modelde tanımlı bir işlev değil. Model tanımlı bir işlev gövdesini gösterdiğini [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), işlevin bağımsız ifade sağlayan kuralları veya veri kaynağındaki desteklenen diller.  
  
 Bir model tanımlı işlev tanımı, şu bilgileri içerir:  
  
-   Bir işlev adı. (Gerekli)  
  
-   Dönüş değerinin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    >  Dönüş değeri, dönüş türü belirtilirse, geçersizdir.  
  
-   Parametre bilgileri. (İsteğe bağlı)  
  
-   Bir [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) işlevinin gövdesi tanımlayan ifade.  
  
 Not model tanımlı işlevleri çıkış parametreleri desteklemez. Böylece model tanımlı işlevleri oluşan bu kısıtlama yerdir.  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.  
  
 ![Yayımlanma tarihi ile model](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL örneği itibaren bir yıl sayılarını döndüren kavramsal modeldeki bir işlevi tanımlayan bir `Book` (Yukarıdaki diyagramda) olarak yayımlandı.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Varlık veri modeli: Basit veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
