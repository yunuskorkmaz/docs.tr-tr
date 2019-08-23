---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 2b4a8a559d7297543812f3c67e3b90d06a011b0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959096"
---
# <a name="facet"></a>facet
Bir *model* , ilkel bir tür özelliği tanımına ayrıntı eklemek için kullanılır. [Özellik](../../../../docs/framework/data/adonet/property.md) tanımı, özellik türü hakkında bilgi içerir, ancak genellikle daha fazla ayrıntı gereklidir. Örneğin, kavramsal modeldeki bir varlık türü, değeri null olarak ayarlanmayabilir türünde `String` bir özelliğe sahip olabilir. Modeller bu ayrıntı düzeyini belirtmenizi sağlar.  
  
 Aşağıdaki tabloda, EDM 'de desteklenen modeller açıklanmaktadır.  
  
> [!NOTE]
> Modellerin tam değerleri ve davranışları, bir EDM uygulamasını kullanan çalışma zamanı ortamına göre belirlenir.  
  
|Kısıtlayan|Açıklama|Uygulandığı öğe:|  
|-----------|-----------------|----------------|  
|`Collation`|Özelliğin değerlerinde karşılaştırma ve sıralama işlemleri gerçekleştirirken kullanılacak harmanlama sırasını (veya sıralama sırasını) belirtir.|`String`|  
|`ConcurrencyMode`|Özellik değerinin iyimser eşzamanlılık denetimleri için kullanılması gerektiğini belirtir.|Tüm ilkel tür özellikleri|  
|`Default`|Örnek oluşturma sırasında hiçbir değer sağlanmadığında özelliğin varsayılan değerini belirtir.|Tüm ilkel tür özellikleri|  
|`FixedLength`|Özellik değerinin uzunluğunun değişebileceğini belirtir.|`Binary`, `String`|  
|`MaxLength`|Özellik değerinin uzunluk üst sınırını belirtir.|`Binary`, `String`|  
|`Nullable`|Özelliğin NULL değere sahip olup olmayacağını belirtir.|Tüm ilkel tür özellikleri|  
|`Precision`|Türündeki `Decimal`özellikler için, bir özellik değerinin sahip olduğu basamak sayısını belirtir. , Ve `Time` türündeki`DateTimeOffset`özellikler için, özellik değeri saniyelik kesirli kısmının basamak sayısını belirtir. `DateTime`|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Özellik değeri için ondalık noktanın sağ tarafındaki basamak sayısını belirtir.|Ondalık|  
|`Unicode`|Özellik değerinin Unicode olarak depolandığını belirtir.|`String`|  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl bir `Book` varlık türünü tanımlar. Modellerinin XML öznitelikleri olarak uygulandığını unutmayın. Model değerleri, hiçbir özelliğin NULL olarak ayarlanabileceği ve `Scale` `Revision` özelliğinin, `Precision` her birinin 29 olarak ayarlandığı anlamına gelebilir.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
