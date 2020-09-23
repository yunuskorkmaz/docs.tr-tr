---
title: 'Nasıl yapılır: Nesneyi Başka Bir Türe Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: b89e996324d9ec22fc243b59502f3d36fefdee60
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090228"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme

`Object` [CType işlevi](../../../language-reference/functions/ctype-function.md)gibi bir dönüştürme anahtar sözcüğünü kullanarak bir değişkeni başka bir veri türüne dönüştürürsünüz.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek bir değişkenini bir `Object` ve öğesine dönüştürür `Integer` `String` .  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Bir `Object` değişkenin içeriğinin belirli bir veri türünde olduğunu biliyorsanız, değişkeni bu veri türüne dönüştürmek daha iyidir. Değişkenini kullanmaya devam ederseniz `Object` , *kutulama* ve *kutudan* çıkarma (bir değer türü için) ya da *geç bağlama* (bir başvuru türü için) uygulanır. Bu işlemler, daha fazla yürütme süresi alır ve performansınızı daha yavaş hale getirir.  
  
## <a name="compile-the-code"></a>Kodu derle  

 Bu örnek şunları gerektirir:  
  
- <xref:System?displayProperty=nameWithType>Ad alanına başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Genişletme ve Daraltma Dönüşümleri](widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](implicit-and-explicit-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](conversions-between-strings-and-other-types.md)
- [Dizi Dönüştürmeler](array-conversions.md)
- [Yapılar](structures.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../language-reference/functions/type-conversion-functions.md)
