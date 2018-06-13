---
title: TryCast İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: d8825b8eee35ea514d4001a6a5c1cc5139c67454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600156"
---
# <a name="trycast-operator-visual-basic"></a>TryCast İşleci (Visual Basic)
Bir özel durum olmayan bir tür dönüştürme işleminin tanıtır.  
  
## <a name="remarks"></a>Açıklamalar  
 Denenen bir dönüştürme başarısız olursa, `CType` ve `DirectCast` her ikisi de throw bir <xref:System.InvalidCastException> hata. Bu, uygulamanızın performansını olumsuz etkileyebilir. `TryCast` döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md), olası bir özel durum işleme gerek kalmadan yerine yalnızca döndürülen sonuç karşı test böylece `Nothing`.  
  
 Kullandığınız `TryCast` anahtar sözcüğü kullandığınız aynı şekilde [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ve [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) anahtar sözcüğü. Bir ifade ilk bağımsız değişken ve ikinci bağımsız değişken olarak dönüştürmek için bir türü olarak sağlayın. `TryCast` yalnızca başvuru türleri, sınıflar ve arabirimler gibi üzerinde çalışır. İki tür arasında bir devralma ya da uygulanmasını ilişkisi gerektirir. Bu tür öğesinden devralmalı ya da diğer uygulamak, anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hataları  
 `TryCast` Devralma veya uygulama hiçbir ilişki var olduğunu algılarsa derleyici hatası oluşturur. Ancak derleyici hatası eksikliği başarılı dönüştürme garanti etmez. İstenen dönüştürme daraltma değilse, çalışma zamanında başarısız olabilir. Bu durumda, `TryCast` döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür Dönüşüm anahtar sözcükleri karşılaştırması aşağıdaki gibidir.  
  
|Anahtar sözcüğü|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)|Tüm veri türleri|Genişletme veya daraltma dönüştürme iki veri türleri arasında tanımlanmalıdır|Oluşturur <xref:System.InvalidCastException>|  
|[DirectCast İşleci](../../../visual-basic/language-reference/operators/directcast-operator.md)|Tüm veri türleri|Bir tür öğesinden devralmalı ya da başka tür|Oluşturur <xref:System.InvalidCastException>|  
|`TryCast`|Yalnızca başvuru türleri|Bir tür öğesinden devralmalı ya da başka tür|Döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
