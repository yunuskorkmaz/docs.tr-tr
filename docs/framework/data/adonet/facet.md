---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 2b263a107eae7c75b035dcb4675725556e0f9c2b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="facet"></a>facet
A *modeli* bir ilkel tür özelliği tanımına ayrıntı eklemek için kullanılır. A [özelliği](../../../../docs/framework/data/adonet/property.md) tanımını özellik türü hakkında bilgi içerir, ancak genellikle daha fazla ayrıntı gereklidir. Örneğin, bir varlık türü kavramsal modelde türünde bir özellik olabilir `String` değeri ayarlanamıyor null. Modeller, bu düzeyde ayrıntı belirtmenize olanak verir.  
  
 Aşağıdaki tabloda EDM desteklenen modellerle açıklanmaktadır.  
  
> [!NOTE]
>  Modelleri davranışlarını ve değerleri tam EDM uygulaması kullanan çalışma zamanı ortamı tarafından belirlenir.  
  
|Modeli|Açıklama|Uygulandığı öğe:|  
|-----------|-----------------|----------------|  
|`Collation`|Harmanlama sırası (veya sıralama) yapılırken kullanılacak karşılaştırma gerçekleştirme ve özellik değerleri operations sıralama belirtir.|`String`|  
|`ConcurrencyMode`|Özelliğinin değeri iyimser eşzamanlılık denetimleri için kullanılması gerektiğini gösterir.|Tüm basit tür özellikleri|  
|`Default`|Örnek oluşturma sırasında herhangi bir değer belirtilirse özelliğinin varsayılan değeri belirtir.|Tüm basit tür özellikleri|  
|`FixedLength`|Özellik değerinin uzunluğu değişebilir olup olmadığını belirtir.|`Binary`, `String`|  
|`MaxLength`|Özellik değerinin uzunluk üst sınırını belirtir.|`Binary`, `String`|  
|`Nullable`|Özelliği bir null değere sahip olup olmadığını belirtir.|Tüm basit tür özellikleri|  
|`Precision`|Tür özellikleri için `Decimal`, bir özellik değeri olabilir basamak sayısını belirtir. Tür özellikleri için `Time`, `DateTime`, ve `DateTimeOffset`, özellik değerinin saniye kesirli kısmı için basamak sayısını belirtir.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Özellik değeri için ondalık basamak sayısını belirtir.|Ondalık|  
|`Unicode`|Özellik değeri Unicode olarak depolanan olup olmadığını gösterir.|`String`|  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlayan bir `Book` varlık türü. Modelleri XML öznitelikleri olarak uygulandığını unutmayın. Bir özellik ayarlanabilir, model değerleri gösterir null ve `Scale` ve `Precision` , `Revision` özelliği her ayarlanır 29 için.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
