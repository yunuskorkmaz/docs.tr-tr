---
title: Model tanımlı işlevi
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 5c91c221735f3385370ec2fbb532d5b3c5dd2898
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="model-defined-function"></a>Model tanımlı işlevi
A *modeli tanımlı işlev* kavramsal modelde tanımlanan bir işlev değil. Model tanımlı bir işlev gövdesi olarak ifade edilen [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), işlevin bağımsız ifade veren kuralları veya veri kaynağında desteklenen diller.  
  
 Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:  
  
-   İşlev adı. (Gerekli)  
  
-   Döndürülen değerin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    >  Dönüş türü belirtilmişse, döndürülen değer geçersizdir.  
  
-   Parametre bilgileri. (İsteğe bağlı)  
  
-   Bir [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) işlevinin gövdesini tanımlayan ifade.  
  
 Model tanımlı işlevler çıkış parametreleri desteklemez unutmayın. Böylece model tanımlı işlevler birleştirilebilen bu kısıtlama yerdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.  
  
 ![Yayımlanma tarihi ile model](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL örneği itibaren yıl numaraları döndürür kavramsal modelde bir işlevi tanımlayan bir `Book` (Yukarıdaki diyagramda) yayımlandı.  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [Varlık Veri Modeli: Basit Veri Türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
