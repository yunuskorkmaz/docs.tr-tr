---
title: DirectCast İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 628ce4f06b91d0f514f71dea3aad8ea0fee6dccf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778553"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast İşleci (Visual Basic)
Devralma veya uygulaması temel bir tür dönüştürme işlemini ortaya çıkarır.  
  
## <a name="remarks"></a>Açıklamalar  
 `DirectCast` Visual Basic çalışma zamanı Yardımcısı yordamları biraz sağlayabilmesi için dönüştürme için daha iyi performans kullanmaz `CType` ve veri türünden dönüştürme yaparken `Object`.  
  
 Kullandığınız `DirectCast` anahtar sözcüğü benzer şekilde, kullandığınız [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) anahtar sözcüğü. Siz ifade ilk bağımsız değişken ve ikinci bağımsız değişken olarak öğesine dönüştürmek için bir tür olarak sağlayın. `DirectCast` iki bağımsız değişkenlerinin veri türleri arasında bir ilişki devralma ya da uygulanmasını gerektirir. Bu, bir türden devralamaz gerekir veya diğer uygulama anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hataları  
 `DirectCast` Devralma ya da uygulanmasını ilişkisi olduğunu algılarsa bir derleyici hatası oluşturur. Ancak, bir derleyici hatası eksikliği başarılı bir dönüştürme garanti etmez. İstenen dönüştürme daraltma, çalışma zamanında başarısız. Bu durumda, çalışma zamanı oluşturur bir <xref:System.InvalidCastException> hata.  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür Dönüşüm anahtar sözcükleri karşılaştırması aşağıdaki gibidir.  
  
|Anahtar sözcüğü|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)|Herhangi bir veri türü|İki veri türleri arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır|Oluşturur <xref:System.InvalidCastException>|  
|`DirectCast`|Herhangi bir veri türü|Bir türden devralamaz veya diğer türü uyguluyor|Oluşturur <xref:System.InvalidCastException>|  
|[TryCast İşleci](../../../visual-basic/language-reference/operators/trycast-operator.md)|Yalnızca başvuru türleri|Bir türden devralamaz veya diğer türü uyguluyor|Döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki kullanımlarını gösterir `DirectCast`, çalıştırma ve biri başarısız biri başarılı.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 Önceki örnekte, çalışma zamanı türü `q` olduğu `Double`. `CType` çünkü başarılı `Double` dönüştürülebilir `Integer`. Ancak, ilk `DirectCast` çalışma zamanı türü için çalışma zamanında başarısız oluyor `Double` ile herhangi bir devralma ilişkisi yoktur `Integer`rağmen bir dönüşümü yok. İkinci `DirectCast` çünkü türünden dönüştürür başarılı <xref:System.Windows.Forms.Form> türüne <xref:System.Windows.Forms.Control>, içinden <xref:System.Windows.Forms.Form> devralır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
