---
title: DirectCast İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 534e94ecc0a394caa2865c2da754ad8f4dbc6f44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="directcast-operator-visual-basic"></a>DirectCast İşleci (Visual Basic)
Devralma veya uygulama temel türü dönüştürme işlemi sunar.  
  
## <a name="remarks"></a>Açıklamalar  
 `DirectCast` Visual Basic çalışma zamanı yardımcı yordamları biraz sağlayabilmesi için dönüştürme için daha iyi performans daha kullanmaz `CType` için ve veri türüne dönüştürülürken `Object`.  
  
 Kullandığınız `DirectCast` anahtar sözcüğü benzer kullandığınız şekilde [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) anahtar sözcüğü. Bir ifade ilk bağımsız değişken ve ikinci bağımsız değişken olarak dönüştürmek için bir türü olarak sağlayın. `DirectCast` iki bağımsız değişkenlerinin veri türleri arasında bir devralma ya da uygulanmasını ilişkisi gerektirir. Bu tür öğesinden devralmalı ya da diğer uygulamak, anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hataları  
 `DirectCast` Devralma veya uygulama hiçbir ilişki var olduğunu algılarsa derleyici hatası oluşturur. Ancak derleyici hatası eksikliği başarılı dönüştürme garanti etmez. İstenen dönüştürme daraltma değilse, çalışma zamanında başarısız olabilir. Bu durumda, çalışma zamanı oluşturur bir <xref:System.InvalidCastException> hata.  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür Dönüşüm anahtar sözcükleri karşılaştırması aşağıdaki gibidir.  
  
|Anahtar sözcüğü|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)|Tüm veri türleri|Genişletme veya daraltma dönüştürme iki veri türleri arasında tanımlanmalıdır|Oluşturur <xref:System.InvalidCastException>|  
|`DirectCast`|Tüm veri türleri|Bir tür öğesinden devralmalı ya da başka tür|Oluşturur <xref:System.InvalidCastException>|  
|[TryCast İşleci](../../../visual-basic/language-reference/operators/trycast-operator.md)|Yalnızca başvuru türleri|Bir tür öğesinden devralmalı ya da başka tür|Döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki kullanımını gösterir `DirectCast`, bir çalışma zamanı ve biri başarısız başarılı olur.  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 Önceki örnekte, çalışma zamanı türü `q` olan `Double`. `CType` çünkü başarılı `Double` dönüştürülebilir `Integer`. Ancak, ilk `DirectCast` çalışma zamanı türü olduğundan çalışma zamanında başarısız `Double` ile herhangi bir devralma ilişkisi yoktur `Integer`rağmen bir dönüştürme yok. İkinci `DirectCast` çünkü türünden dönüştürür başarılı <xref:System.Windows.Forms.Form> yazmak için <xref:System.Windows.Forms.Control>, içinden <xref:System.Windows.Forms.Form> devralır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
