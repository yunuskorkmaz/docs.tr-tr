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
ms.openlocfilehash: f25caec43b7118b7b64db1b14516b0c5ea80f4f6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504884"
---
# <a name="value-types-and-reference-types"></a>Değer Türleri ve Başvuru Türleri
Visual Basic'te tür iki tür vardır: başvuru türleri ve değer türleri. Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir. Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir. Değer türleri ile her değişkenin kendi veri kopyası vardır ve yapılan işlemlerin diğerini etkilemesi için bir değişken üzerinde değil (dışındaki durumunda [parametreleri ByRef değiştiricisi](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Değer Türleri  
 Bir veri türü olan bir *değer türü* kendi bellek ayırma verileri tutuyorsa. Değer türleri aşağıdakileri kapsamaktadır:  
  
- Tüm sayısal veri türleri  
  
- `Boolean`, `Char`, ve `Date`  
  
- Başvuru türleri üyelerinin olması durumunda bile tüm yapıları  
  
- Her zaman kendi temel türü olduğundan numaralandırmalar `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, veya `ULong`  
  
 Başvuru türü üyeleri içeren olsa bile her bir değer türü yapısıdır. Bu nedenle, değer türleri gibi `Char` ve `Integer` .NET Framework yapıları tarafından uygulanır.  
  
 Ayrılmış anahtar sözcüğü, örneğin,'ı kullanarak bir değer türü bildirebilirsiniz `Decimal`. Ayrıca `New` anahtar sözcüğü, bir değer türü başlatılamadı. Tür parametreleri alan bir oluşturucu sahipse, bu özellikle yararlıdır. Bunun bir örneği <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> yeni bir derleme Oluşturucu `Decimal` sağlanan parçalarından değeri.  
  
## <a name="reference-types"></a>Başvuru Türleri  
 A *başvuru türüne* başvuru verilerini depolar. Başvuru türleri aşağıdakileri kapsamaktadır:  
  
- `String`  
  
- Tüm diziler, kendi öğeleri değer türleri olsa bile  
  
- Sınıfı, gibi türleri <xref:System.Windows.Forms.Form>  
  
- Temsilciler  
  
 Bir sınıf bir *başvuru türüne*. Üyeleri, değer türleri olsa bile, her dizide bir başvuru türü olduğunu unutmayın.  
  
 Her bir başvuru türü temel alınan bir .NET Framework sınıfı temsil eder. bu yana kullanmalısınız [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) başlattığınızda, anahtar sözcüğü. Aşağıdaki deyim, bir dizi başlatır.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Türleri öğeleri  
 Bunların hiçbirine olarak bildirilen bir öğe için bir veri türü belirtilemez çünkü aşağıdaki programlama öğeleri türleri olarak nitelendirmeyin:  
  
- Ad Alanları  
  
- Modüller  
  
- Olaylar  
  
- Özellikler ve yordamlar  
  
- Değişkenleri, sabitleri ve alanlar  
  
## <a name="working-with-the-object-data-type"></a>Nesne veri türü ile çalışma  
 Bir başvuru türü veya değer türü bir değişkene atayabilirsiniz `Object` veri türü. Bir `Object` değişken her zaman bir başvuru veri hiçbir zaman kendisi tutar. Ancak, bir değer türüne atarsanız bir `Object` kendi verilerini tutan gibi değişken davranır. Daha fazla bilgi için [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Olup bulabilirsiniz bir `Object` değişkeni hareket bir başvuru türü veya değer türü olarak geçirerek <xref:Microsoft.VisualBasic.Information.IsReference%2A> yönteminde <xref:Microsoft.VisualBasic.Information> sınıfının <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> döndürür `True` durumunda içeriğinin `Object` değişkeninin bir başvuru türü temsil eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boş Değer Atanabilen Değer Türleri](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
