---
title: TryCast İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dd50a23f09fa5dd49b86eefe163cea20430e2360
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981289"
---
# <a name="trycast-operator-visual-basic"></a>TryCast İşleci (Visual Basic)
Bir özel durum oluşturmaz bir tür dönüştürme işlemini ortaya çıkarır.  
  
## <a name="remarks"></a>Açıklamalar  
 Denenen bir dönüştürme başarısız olursa `CType` ve `DirectCast` hem throw bir <xref:System.InvalidCastException> hata. Bu, uygulamanızın performansını olumsuz yönde etkileyebilir. `TryCast` döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md), olası bir özel durumu işlemek zorunda kalmak yerine, yalnızca döndürülen karşı test sonucu böylece `Nothing`.  
  
 Kullandığınız `TryCast` anahtar sözcüğü kullandığınız aynı şekilde [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ve [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) anahtar sözcüğü. Siz ifade ilk bağımsız değişken ve ikinci bağımsız değişken olarak öğesine dönüştürmek için bir tür olarak sağlayın. `TryCast` yalnızca başvuru türleri sınıflar ve arabirimler gibi çalışır. İki tür arasında bir ilişki devralma ya da uygulanmasını gerektirir. Bu, bir türden devralamaz gerekir veya diğer uygulama anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hataları  
 `TryCast` Devralma ya da uygulanmasını ilişkisi olduğunu algılarsa bir derleyici hatası oluşturur. Ancak, bir derleyici hatası eksikliği başarılı bir dönüştürme garanti etmez. İstenen dönüştürme daraltma, çalışma zamanında başarısız. Böyle bir durumda `TryCast` döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür Dönüşüm anahtar sözcükleri karşılaştırması aşağıdaki gibidir.  
  
|Anahtar sözcüğü|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)|Herhangi bir veri türü|İki veri türleri arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır|Oluşturur <xref:System.InvalidCastException>|  
|[DirectCast İşleci](../../../visual-basic/language-reference/operators/directcast-operator.md)|Herhangi bir veri türü|Bir türden devralamaz veya diğer türü uyguluyor|Oluşturur <xref:System.InvalidCastException>|  
|`TryCast`|Yalnızca başvuru türleri|Bir türden devralamaz veya diğer türü uyguluyor|Döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
