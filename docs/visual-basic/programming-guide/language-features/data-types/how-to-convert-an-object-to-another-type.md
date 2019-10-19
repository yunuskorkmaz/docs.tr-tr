---
title: "Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 39083fc55d30e24c357ec162a15466f81655f4c8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582337"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme
[CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)gibi bir dönüştürme anahtar sözcüğünü kullanarak bir `Object` değişkenini başka bir veri türüne dönüştürürsünüz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir `Object` değişkenini `Integer` ve `String` dönüştürür.  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Bir `Object` değişkeninin içeriğinin belirli bir veri türünde olduğunu biliyorsanız, değişkeni bu veri türüne dönüştürmek daha iyidir. @No__t_0 değişkenini kullanmaya devam ederseniz, *kutulama* ve *kutudan* çıkarma (bir değer türü için) ya da *geç bağlama* (bir başvuru türü için) uygulanır. Bu işlemler, daha fazla yürütme süresi alır ve performansınızı daha yavaş hale getirir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- @No__t_0 ad alanına bir başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
