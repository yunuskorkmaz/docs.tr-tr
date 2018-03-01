---
title: "DirectCast İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b81abea364e328b831ee98c3b847161c3f7dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="directcast-operator-visual-basic"></a>DirectCast İşleci (Visual Basic)
Devralma veya uygulama temel türü dönüştürme işlemi sunar.  
  
## <a name="remarks"></a>Açıklamalar  
 `DirectCast`Visual Basic çalışma zamanı yardımcı yordamları biraz sağlayabilmesi için dönüştürme için daha iyi performans daha kullanmaz `CType` için ve veri türüne dönüştürülürken `Object`.  
  
 Kullandığınız `DirectCast` anahtar sözcüğü benzer kullandığınız şekilde [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) anahtar sözcüğü. Bir ifade ilk bağımsız değişken ve ikinci bağımsız değişken olarak dönüştürmek için bir türü olarak sağlayın. `DirectCast`iki bağımsız değişkenlerinin veri türleri arasında bir devralma ya da uygulanmasını ilişkisi gerektirir. Bu tür öğesinden devralmalı ya da diğer uygulamak, anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hataları  
 `DirectCast`Devralma veya uygulama hiçbir ilişki var olduğunu algılarsa derleyici hatası oluşturur. Ancak derleyici hatası eksikliği başarılı dönüştürme garanti etmez. İstenen dönüştürme daraltma değilse, çalışma zamanında başarısız olabilir. Bu durumda, çalışma zamanı oluşturur bir <xref:System.InvalidCastException> hata.  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür Dönüşüm anahtar sözcükleri karşılaştırması aşağıdaki gibidir.  
  
|Anahtar sözcüğü|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md)|Tüm veri türleri|Genişletme veya daraltma dönüştürme iki veri türleri arasında tanımlanmalıdır|Oluşturur<xref:System.InvalidCastException>|  
|`DirectCast`|Tüm veri türleri|Bir tür öğesinden devralmalı ya da başka tür|Oluşturur<xref:System.InvalidCastException>|  
|[TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md)|Yalnızca başvuru türleri|Bir tür öğesinden devralmalı ya da başka tür|Döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki kullanımını gösterir `DirectCast`, bir çalışma zamanı ve biri başarısız başarılı olur.  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 Önceki örnekte, çalışma zamanı türü `q` olan `Double`. `CType`çünkü başarılı `Double` dönüştürülebilir `Integer`. Ancak, ilk `DirectCast` çalışma zamanı türü olduğundan çalışma zamanında başarısız `Double` ile herhangi bir devralma ilişkisi yoktur `Integer`rağmen bir dönüştürme yok. İkinci `DirectCast` çünkü türünden dönüştürür başarılı <xref:System.Windows.Forms.Form> yazmak için <xref:System.Windows.Forms.Control>, içinden <xref:System.Windows.Forms.Form> devralır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [Genişletme ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
