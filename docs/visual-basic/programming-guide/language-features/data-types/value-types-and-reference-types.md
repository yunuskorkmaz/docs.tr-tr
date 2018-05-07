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
ms.openlocfilehash: 9456316f71a213905bcb50336533c4e618f5174a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="value-types-and-reference-types"></a>Değer Türleri ve Başvuru Türleri
Visual Basic veri türleri sınıflandırmalarına göre uygulanır. Visual Basic veri türleri, belirli türde bir değişken kendi veri veya veri için bir işaretçi depolar göre sınıflandırılabilir. Kendi verilerini depolayan ise bir *değer türü*; başka bir yerde bu bellek verileri için bir işaretçi barındırıyorsa bir *başvuru türüne*.  
  
## <a name="value-types"></a>Değer Türleri  
 Bir veri türü olan bir *değer türü* kendi bellek ayırma içindeki verilere tutuyorsa. Değer türleri şunlardır:  
  
-   Tüm sayısal veri türleri  
  
-   `Boolean`, `Char`, ve `Date`  
  
-   Başvuru türleri üyeleri olan olsa bile tüm yapıları  
  
-   Kendi temel alınan türü her zaman olduğundan numaralandırmalar `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, veya `ULong`  
  
 Başvuru türü üyeleri içerse bile, her bir değer türü yapısıdır. Bu nedenle, değer türleri gibi `Char` ve `Integer` .NET Framework yapıları tarafından uygulanır.  
  
 Ayrılmış bir anahtar sözcük, örneğin, kullanarak bir değer türü bildirebilirsiniz `Decimal`. Aynı zamanda `New` anahtar sözcüğü bir değer türü başlatılamadı. Bu tür parametreler isteyen bir kurucusunun özellikle yararlıdır. Bunun bir örneği <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> yeni yapılar Oluşturucusu `Decimal` sağlanan bölümlerinden değeri.  
  
## <a name="reference-types"></a>Başvuru Türleri  
 A *başvuru türüne* verilerini tutan başka bir bellek konumunu gösteren bir işaretçi içeriyor. Başvuru türleri şunlardır:  
  
-   `String`  
  
-   Değer türleri kendi öğeleridir olsa bile tüm diziler  
  
-   Sınıf türleri, gibi <xref:System.Windows.Forms.Form>  
  
-   Temsilciler  
  
 Bir sınıf bir *başvuru türüne*. Bu nedenle, başvuru türleri gibi `Object` ve `String` tarafından desteklenen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıfları. Değer türleri üyeleri olsa bile, her dizi bir başvuru türü olduğunu unutmayın.  
  
 Her başvuru türündeki temel alınan bir .NET Framework sınıfı temsil ettiği kullanmalısınız [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) , Initialize when anahtar sözcüğü. Aşağıdaki deyim, bir dizi başlatır.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Türleri olmayan öğeler  
 Bildirilen öğe için bir veri türü olarak hiçbirini belirtilemez çünkü aşağıdaki programlama öğeleri türleri olarak nitelemek değil:  
  
-   Ad Alanları  
  
-   Modüller  
  
-   Olaylar  
  
-   Özellikler ve yordamları  
  
-   Değişkenlerinin, sabitleri ve alanlar  
  
## <a name="working-with-the-object-data-type"></a>Nesne veri türü ile çalışma  
 Bir değişken için bir başvuru türü veya bir değer türü atayabilirsiniz `Object` veri türü. Bir `Object` değişkeni verileri verilerin kendisini hiçbir zaman, her zaman bir işaretçi tutar. Ancak, bir değer türü atarsanız bir `Object` kendi verilerini varmış gibi değişken, davranır. Daha fazla bilgi için bkz: [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Tanımlanmadığını bulabileceğiniz bir `Object` değişken işlevi gören bir başvuru türü veya bir değer türü olarak geçirerek <xref:Microsoft.VisualBasic.Information.IsReference%2A> yönteminde <xref:Microsoft.VisualBasic.Information> sınıfının <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> döndürür `True` varsa içeriğini `Object` değişkeni bir başvuru türü temsil eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Boş Değer Atanabilen Değer Türleri](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
