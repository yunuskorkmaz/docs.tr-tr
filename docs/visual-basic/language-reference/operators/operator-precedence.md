---
title: "Visual Basic'de İşleç Önceliği"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c0fb466b404cafdd4b91d061971fd683375c715
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic'de İşleç Önceliği
Çeşitli işlemler bir ifadede gerçekleştiğinde, her bölüm değerlendirilir ve adlı önceden belirlenmiş bir sırayla çözülmüş *İşleç önceliği*.  
  
## <a name="precedence-rules"></a>Öncelik kuralları  
 İfadeleri birden fazla kategorisinden işleçler içeriyorsa, bunlar aşağıdaki kurallara göre değerlendirilir:  
  
-   Aritmetik ve birleştirme işleçleri aşağıdaki bölümde açıklanan öncelik sırasını yoksa ve tüm mantıksal, karşılaştırma büyük önceliğe ve bit düzeyinde işleçler.  
  
-   Tüm Karşılaştırma işleçleri eşit önceliğe ve tüm mantıksal ve bit düzeyinde işleçler büyük önceliğe ancak aritmetik ve birleştirme işleçleri daha düşük önceliğe sahip.  
  
-   Aşağıdaki bölümde açıklanan öncelik sırasını mantıksal ve bit düzeyinde işleçler sahiptir ve tüm aritmetik, birleştirme ve Karşılaştırma işleçleri daha düşük önceliğe sahip.  
  
-   Eşit önceliğe sahip işleçler soldan sağa değerlendirilen ifade göründükleri sırada.  
  
## <a name="precedence-order"></a>Öncelik sırası  
 İşleç önceliği aşağıdaki sırayla değerlendirilir:  
  
### <a name="await-operator"></a>Await İşleci  
 await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Aritmetik ve birleştirme işleçleri  
 Üs (`^`)  
  
 Birli kimlik ve değilleme (`+`, `–`)  
  
 Çarpma ve kayan nokta bölme (`*`, `/`)  
  
 Tamsayı bölme (`\`)  
  
 Modulus aritmetik (`Mod`)  
  
 Toplama ve çıkarma (`+`, `–`)  
  
 Dize birleştirmesi (`&`)  
  
 Aritmetik bit kaydırma (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Karşılaştırma İşleçleri  
 Tüm Karşılaştırma işleçleri (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Mantıksal ve bit düzeyinde işleçler  
 Değilleme (`Not`)  
  
 Birlikte (`And`, `AndAlso`)  
  
 Kapsayıcı ayrım (`Or`, `OrElse`)  
  
 Özel ayrım (`Xor`)  
  
### <a name="comments"></a>Açıklamalar  
 `=` İşlecidir yalnızca eşitlik karşılaştırma işleci, atama işleci.  
  
 Dize birleştirme işleci (`&`) bir aritmetik işleç değildir, ancak içinde öncelik aritmetik işleçler gruplandırılır.  
  
 `Is` Ve `IsNot` işleçler şunlardır: nesne başvurusu Karşılaştırma işleçleri. İki nesnenin değerlerini karşılaştırmak değil; yalnızca iki nesne değişkenleri aynı nesne örneğine başvuru olup olmadığını belirlemek için denetleyin.  
  
## <a name="associativity"></a>İlişkilendirilebilirlik  
 Eşit öncelik işleçleri birlikte bir ifade örneğin çarpma ve bölme göründüğünde, soldan sağa karşılaştığında gibi derleyici her işlemi değerlendirir. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 İlk ifade 96 bölme değerlendirir / (12'de sonuçlarını) 8'i ve ardından bölme 12 / üç içinde sonuçları 4. Derleyici işlemler için değerlendirildiği `n1` Bu sipariş için açıkça belirtildiğinde soldan sağa değerlendirme aynıdır `n2`. Her ikisi de `n1` ve `n2` üç sonucunu sahip. Bunun aksine, `n3` 48, sonucunu sahip parantez 8 değerlendirmek için derleyici zorla olduğundan / 4 ilk.  
  
 Bu davranış nedeniyle işleçleri yereldir *ilişkilendirilebilir sol* içinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="overriding-precedence-and-associativity"></a>Öncelik ve birleşim geçersiz kılma  
 Başkalarının önce değerlendirilecek bir ifade bazı bölümleri zorlamak için parantez kullanabilirsiniz. Bu öncelik sırasını ve sol birleşim geçersiz kılabilirsiniz. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]her zaman dışındaki önce parantez içine işlemleri gerçekleştirir. Parantez içinde parantez kullanmadığınız sürece ancak parantez içinde normal öncelik ve birleşim, tutar. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Is işleci](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot işleci](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Like işleci](../../../visual-basic/language-reference/operators/like-operator.md)  
 [TypeOf işleci](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Await işleci](../../../visual-basic/language-reference/operators/await-operator.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
