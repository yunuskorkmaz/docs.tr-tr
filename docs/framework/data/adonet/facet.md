---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 9353b143a328e0fb183b7870332462a0a2c91b10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094508"
---
# <a name="facet"></a>facet
A *modeli* ayrıntılı bir basit türü özellik tanımı eklemek için kullanılır. A [özelliği](../../../../docs/framework/data/adonet/property.md) tanımı özellik türü ile ilgili bilgiler içerir, ancak genellikle daha fazla ayrıntı gereklidir. Örneğin, bir varlık türü kavramsal modelde vlastnost typu olabilir `String` değeri ayarlanamıyor null. Modelleri, bu düzeyde ayrıntı belirtmenizi sağlar.  
  
 Aşağıdaki tabloda EDM içinde desteklenmeyen özellikleri açıklanmaktadır.  
  
> [!NOTE]
>  Modelleri, davranışları ve tam değerleri kullanan bir EDM uygulama çalışma zamanı ortamı tarafından belirlenir.  
  
|modeli|Açıklama|Uygulandığı öğe:|  
|-----------|-----------------|----------------|  
|`Collation`|Harmanlama dizisi (veya sıralama) yapılırken kullanılacak karşılaştırma gerçekleştirme ve özellik değerleri üzerinde işlem sıralama belirtir.|`String`|  
|`ConcurrencyMode`|Özelliğinin değeri için iyimser eşzamanlılık denetimlerinin kullanılması gerektiğini gösterir.|Tüm temel türü özellikleri|  
|`Default`|Örnek oluşturma sırasında herhangi bir değer sağlanmazsa, özelliğin varsayılan değerini belirtir.|Tüm temel türü özellikleri|  
|`FixedLength`|Özellik değerinin uzunluğu değişebilir olup olmadığını belirtir.|`Binary`, `String`|  
|`MaxLength`|Özellik değeri en büyük uzunluğunu belirtir.|`Binary`, `String`|  
|`Nullable`|Özelliği null değere sahip olup olamayacağını belirtir.|Tüm temel türü özellikleri|  
|`Precision`|Tür özellikleri için `Decimal`, bir özellik değeri olabilir basamak sayısını belirtir. Tür özellikleri için `Time`, `DateTime`, ve `DateTimeOffset`, özellik değerinin saniye kesirli kısmını için basamak sayısını belirtir.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Özellik değeri ondalık noktasının sağındaki basamak sayısını belirtir.|Ondalık|  
|`Unicode`|Özellik değeri Unicode olarak mi depolanacağını belirtir.|`String`|  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlayan bir `Book` varlık türü. Modelleri, XML özniteliği uygulandığını unutmayın. Bir özellik ayarlanabilir, modeli değerleri belirtmek null ve `Scale` ve `Precision` , `Revision` özelliği her ayarlanır 29 için.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
