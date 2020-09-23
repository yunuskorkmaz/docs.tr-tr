---
title: Değer Türleri ve Başvuru Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 72cb1455300e1ff00d9d558aa5a9df95f32aa7b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090124"
---
# <a name="value-types-and-reference-types"></a>Değer Türleri ve Başvuru Türleri

Visual Basic iki tür tür vardır: başvuru türleri ve değer türleri. Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir. Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir. Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişken üzerindeki işlemler diğerini etkileme ( [parametrelerde ByRef değiştirici](../../../language-reference/modifiers/byref.md)olması dışında) mümkün değildir.
  
## <a name="value-types"></a>Değer Türleri  

 Veri türü, verileri kendi bellek ayırması içinde tutuyorsa bir *değer türüdür* . Değer türleri şunları içerir:  
  
- Tüm sayısal veri türleri  
  
- `Boolean`, `Char` ve `Date`  
  
- Üyeleri başvuru türleri olsa bile tüm yapılar  
  
- Numaralandırmalar, temel alınan türü her zaman,,,,,, `SByte` `Short` `Integer` `Long` `Byte` `UShort` `UInteger` , veya `ULong`  
  
 Her yapı, başvuru türü üyeleri içerse de bir değer türüdür. Bu nedenle, ve gibi değer türleri `Char` `Integer` .NET Framework yapılar tarafından uygulanır.  
  
 Ayrılmış anahtar sözcüğünü kullanarak bir değer türü bildirebilirsiniz, örneğin, `Decimal` . `New`Anahtar sözcüğünü bir değer türünü başlatmak için de kullanabilirsiniz. Bu özellikle, türün parametreleri alan bir Oluşturucusu varsa yararlıdır. Bu, <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> sağlanan bölümlerden yeni bir değer oluşturan Oluşturucu örneğidir `Decimal` .  
  
## <a name="reference-types"></a>Başvuru Türleri  

 Bir *başvuru türü* , verilerine bir başvuru depolar. Başvuru türleri şunları içerir:  
  
- `String`  
  
- Tüm diziler, öğeleri değer türseler bile  
  
- Gibi sınıf türleri <xref:System.Windows.Forms.Form>  
  
- Temsilciler  
  
 Sınıf bir *başvuru türüdür*. Her dizi, üyeleri değer türleri olsa bile bir başvuru türü olduğunu unutmayın.  
  
 Her başvuru türü temeldeki bir .NET Framework sınıfını temsil ettiğinden, onu başlattığınızda [New Operator](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanmanız gerekir. Aşağıdaki ifade bir diziyi başlatır.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Türler olmayan öğeler  

 Aşağıdaki programlama öğeleri tür olarak nitelemez, çünkü bunlardan herhangi birini tanımlanmış bir öğe için veri türü olarak belirtemezsiniz:  
  
- Ad Alanları  
  
- Modüller  
  
- Ekinlikler  
  
- Özellikler ve yordamlar  
  
- Değişkenler, sabitler ve alanlar  
  
## <a name="working-with-the-object-data-type"></a>Nesne veri türüyle çalışma  

 Veri türü değişkenine bir başvuru türü veya değer türü atayabilirsiniz `Object` . Değişken, hiçbir zaman verilerin `Object` kendisi olan bir başvuruya sahiptir. Ancak, bir değişkene bir değer türü atarsanız `Object` , kendi verilerini tutan gibi davranır. Daha fazla bilgi için bkz. [nesne veri türü](../../../language-reference/data-types/object-data-type.md).  
  
 Bir `Object` değişkenin bir başvuru türü olarak hareket ettiğini veya bir değer türünün, <xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information> ad alanının sınıfındaki yöntemine geçirerek bir değer türü olup olmadığını görebilirsiniz <xref:Microsoft.VisualBasic?displayProperty=nameWithType> . <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>`True` `Object` değişkenin içeriği bir başvuru türünü temsil ediyorsa, döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Null yapılabilir değer türleri](nullable-value-types.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Structure Yapısı](../../../language-reference/statements/structure-statement.md)
- [Veri Türlerinin Etkili Kullanımı](efficient-use-of-data-types.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
- [Veri türleri](index.md)
