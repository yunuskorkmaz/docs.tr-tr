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
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582640"
---
# <a name="value-types-and-reference-types"></a>Değer Türleri ve Başvuru Türleri
Visual Basic iki tür tür vardır: başvuru türleri ve değer türleri. Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir. Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir. Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişken üzerindeki işlemler diğerini etkileme ( [parametrelerde ByRef değiştirici](../../../language-reference/modifiers/byref.md)olması dışında) mümkün değildir.
  
## <a name="value-types"></a>Değer Türleri  
 Veri türü, verileri kendi bellek ayırması içinde tutuyorsa bir *değer türüdür* . Değer türleri şunları içerir:  
  
- Tüm sayısal veri türleri  
  
- `Boolean`, `Char` ve `Date`  
  
- Üyeleri başvuru türleri olsa bile tüm yapılar  
  
- Numaralandırmalar, temel alınan türü her zaman `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` veya `ULong`  
  
 Her yapı, başvuru türü üyeleri içerse de bir değer türüdür. Bu nedenle, `Char` ve `Integer` gibi değer türleri .NET Framework yapıları tarafından uygulanır.  
  
 Ayrılmış anahtar sözcüğünü kullanarak bir değer türü bildirebilirsiniz, örneğin, `Decimal`. Değer türünü başlatmak için `New` anahtar sözcüğünü de kullanabilirsiniz. Bu özellikle, türün parametreleri alan bir Oluşturucusu varsa yararlıdır. Bunun bir örneği, sağlanan bölümlerden yeni bir `Decimal` değeri oluşturan <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> oluşturucusudur.  
  
## <a name="reference-types"></a>Başvuru Türleri  
 Bir *başvuru türü* , verilerine bir başvuru depolar. Başvuru türleri şunları içerir:  
  
- `String`  
  
- Tüm diziler, öğeleri değer türseler bile  
  
- @No__t_0 gibi sınıf türleri  
  
- Temsilciler  
  
 Sınıf bir *başvuru türüdür*. Her dizi, üyeleri değer türleri olsa bile bir başvuru türü olduğunu unutmayın.  
  
 Her başvuru türü temeldeki bir .NET Framework sınıfını temsil ettiğinden, onu başlattığınızda [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü kullanmanız gerekir. Aşağıdaki ifade bir diziyi başlatır.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Türler olmayan öğeler  
 Aşağıdaki programlama öğeleri tür olarak nitelemez, çünkü bunlardan herhangi birini tanımlanmış bir öğe için veri türü olarak belirtemezsiniz:  
  
- Ad Alanları  
  
- Modüller  
  
- Olaylar  
  
- Özellikler ve yordamlar  
  
- Değişkenler, sabitler ve alanlar  
  
## <a name="working-with-the-object-data-type"></a>Nesne veri türüyle çalışma  
 @No__t_0 veri türü değişkenine bir başvuru türü veya değer türü atayabilirsiniz. Bir `Object` değişken her zaman veriye bir başvuru barındırır, hiçbir zaman verilerin kendisi değildir. Ancak, bir `Object` değişkenine bir değer türü atarsanız, kendi verilerini tutan gibi davranır. Daha fazla bilgi için bkz. [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Bir `Object` değişkeninin, <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanının <xref:Microsoft.VisualBasic.Information> sınıfındaki <xref:Microsoft.VisualBasic.Information.IsReference%2A> yöntemine geçirerek bir başvuru türü veya değer türü olarak davranıp davranmadığını fark edebilirsiniz. `Object` değişkeninin içeriği bir başvuru türünü temsil ediyorsa <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> `True` döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boş Değer Atanabilen Değer Türleri](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
