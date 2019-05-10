---
title: Visual Basic'de İşleç Önceliği
ms.date: 07/20/2015
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
ms.openlocfilehash: 95505fd593881ff27418c69550952d072b4e3949
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628866"
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic'de İşleç Önceliği
Çeşitli işlemler bir ifadede, her parça değerlendirilir ve adlı belirlenmiş bir sırayla çözümlenen *İşleç önceliği*.  
  
## <a name="precedence-rules"></a>Öncelik kuralları  
 İfadeleri işleçler birden fazla kategorisinden içeriyorsa, bunlar aşağıdaki kurallara göre değerlendirilir:  
  
- Aritmetik ve birleştirme işleçleri aşağıdaki bölümde anlatılan öncelik sırasını, ve tüm mantıksal, karşılaştırma büyük önceliğe ve bit düzeyinde işleçler sahiptir.  
  
- Tüm Karşılaştırma işleçleri eşit önceliğe ve tüm mantıksal ve bit düzeyinde işleçler daha yüksek bir önceliğe ancak aritmetik ve birleştirme işleçleri daha düşük önceliğe sahiptir.  
  
- Aşağıdaki bölümde anlatılan öncelik sırası mantıksal ve bit düzeyinde işleçler sahiptir ve tüm aritmetik, birleştirme ve Karşılaştırma işleçleri daha düşük önceliğe sahiptir.  
  
- Eşit önceliğe sahip işleçler soldan sağa doğru değerlendirilir ifadede göründükleri sırayla.  
  
## <a name="precedence-order"></a>Öncelik sırası  
 İşleçler, öncelik aşağıdaki sırada değerlendirilir:  
  
### <a name="await-operator"></a>Await İşleci  
 await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Aritmetik ve birleştirme işleçleri  
 Üs olarak gösterme (`^`)  
  
 Birli kimlik ve değilleme (`+`, `–`)  
  
 Çarpma ve kayan nokta bölme (`*`, `/`)  
  
 Tamsayı bölme (`\`)  
  
 Modulus aritmetik (`Mod`)  
  
 Toplama ve çıkarma (`+`, `–`)  
  
 Dize birleştirmesi (`&`)  
  
 Aritmetik bit kaydırma (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Karşılaştırma İşleçleri  
 Tüm Karşılaştırma işleçleri (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Mantıksal ve Bit Düzeyinde İşleçler  
 Değilleme (`Not`)  
  
 Birlikte (`And`, `AndAlso`)  
  
 Kapsamlı veya işlecini (`Or`, `OrElse`)  
  
 Dışlayıcı veya işlecini (`Xor`)  
  
### <a name="comments"></a>Açıklamalar  
 `=` İşleci, yalnızca eşitlik karşılaştırma işleci atama işleci.  
  
 Dize birleştirme işlecini (`&`) bir aritmetik işleç değil, ancak önceliği aritmetik işleçler gruplandırılır.  
  
 `Is` Ve `IsNot` işleçler şunlardır: nesne başvuru Karşılaştırma işleçleri. İki nesne değerleri karşılaştırılabilir değil; yalnızca iki nesne değişkenini aynı nesne örneğine başvurmadığını belirlemek için denetleyin.  
  
## <a name="associativity"></a>İlişkilendirilebilirlik  
 Eşit önceliğe sahip işleçler birlikte bir ifadede, örneğin çarpma ve bölme görüntülendiğinde, soldan sağa karşılaştığında gibi derleyici her işlem değerlendirir. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 Bölme 96 ilk ifade değerlendirir / (12'de sonuçları) 8'i ve ardından bölme 12 / üç sonuçları 4 '. Derleyici işlemlerinde değerlendirdiğinden `n1` Bu sipariş için açıkça belirtildiğinde soldan sağa değerlendirme aynıdır `n2`. Her ikisi de `n1` ve `n2` üç sonucunu sahip. Bunun aksine, `n3` parantezler 8 değerlendirmek için derleyiciyi sonucu 48, sahip / 4 ilk.  
  
 Bu davranış nedeniyle, işleçler olduğu söylenir *ilişkilendirilebilir sol* Visual Basic'te.  
  
## <a name="overriding-precedence-and-associativity"></a>Geçersiz kılma öncelik ve İlişkisellik  
 Bazı bölümlerini önce değerlendirilecek bir ifade zorlamak için parantez kullanabilirsiniz. Öncelik sırası hem sol ilişkilendirilebilirliği geçersiz kılabilirsiniz. Visual Basic, her zaman önce dışındaki parantez içine alınan işlemleri gerçekleştirir. Parantez içindeki parantez kullanmadığınız sürece ancak parantezler içinde bu normal öncelik ve ilişkisellik, tutar. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Like İşleci](../../../visual-basic/language-reference/operators/like-operator.md)
- [TypeOf İşleci](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Await İşleci](../../../visual-basic/language-reference/operators/await-operator.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
