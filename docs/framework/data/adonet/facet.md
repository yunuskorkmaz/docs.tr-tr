---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: b9ef2276f988923fe83cefce910e8c3685cb9da9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156452"
---
# <a name="facet"></a>facet

Bir *model* , ilkel bir tür özelliği tanımına ayrıntı eklemek için kullanılır. [Özellik](property.md) tanımı, özellik türü hakkında bilgi içerir, ancak genellikle daha fazla ayrıntı gereklidir. Örneğin, kavramsal modeldeki bir varlık türü, `String` değeri null olarak ayarlanmayabilir türünde bir özelliğe sahip olabilir. Modeller bu ayrıntı düzeyini belirtmenizi sağlar.  
  
 Aşağıdaki tabloda, EDM 'de desteklenen modeller açıklanmaktadır.  
  
> [!NOTE]
> Modellerin tam değerleri ve davranışları, bir EDM uygulamasını kullanan çalışma zamanı ortamına göre belirlenir.  
  
|Kısıtlayan|Açıklama|Şunlara uygulanır|  
|-----------|-----------------|----------------|  
|`Collation`|Özelliğin değerlerinde karşılaştırma ve sıralama işlemleri gerçekleştirirken kullanılacak harmanlama sırasını (veya sıralama sırasını) belirtir.|`String`|  
|`ConcurrencyMode`|Özellik değerinin iyimser eşzamanlılık denetimleri için kullanılması gerektiğini belirtir.|Tüm ilkel tür özellikleri|  
|`Default`|Örnek oluşturma sırasında hiçbir değer sağlanmadığında özelliğin varsayılan değerini belirtir.|Tüm ilkel tür özellikleri|  
|`FixedLength`|Özellik değerinin uzunluğunun değişebileceğini belirtir.|`Binary`, `String`|  
|`MaxLength`|Özellik değerinin uzunluk üst sınırını belirtir.|`Binary`, `String`|  
|`Nullable`|Özelliğin NULL değere sahip olup olmayacağını belirtir.|Tüm ilkel tür özellikleri|  
|`Precision`|Türündeki özellikler için `Decimal` , bir özellik değerinin sahip olduğu basamak sayısını belirtir. , Ve türündeki özellikler için, `Time` `DateTime` `DateTimeOffset` özellik değeri saniyelik kesirli kısmının basamak sayısını belirtir.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Özellik değeri için ondalık noktanın sağ tarafındaki basamak sayısını belirtir.|Ondalık|  
|`Unicode`|Özellik değerinin Unicode olarak depolandığını belirtir.|`String`|  
  
## <a name="example"></a>Örnek  

 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL bir `Book` varlık türünü tanımlar. Modellerinin XML öznitelikleri olarak uygulandığını unutmayın. Model değerleri, hiçbir özelliğin NULL olarak ayarlanabileceği ve `Scale` `Precision` özelliğinin, `Revision` her birinin 29 olarak ayarlandığı anlamına gelebilir.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
