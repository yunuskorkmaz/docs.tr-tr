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
ms.openlocfilehash: df40aced45442c9c7895c8d10ece64b21e292508
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659921"
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic'de İşleç Önceliği
Bir ifadede birkaç işlem gerçekleştiğinde, her parça, *işleç önceliği*olarak adlandırılan önceden belirlenmiş bir sırada değerlendirilir ve çözümlenir.

## <a name="precedence-rules"></a>Öncelik kuralları
 İfadeler birden fazla kategoriden işleçler içerdiğinde, bunlar aşağıdaki kurallara göre değerlendirilir:

- Aritmetik ve birleştirme işleçleri aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümü karşılaştırma, mantıksal ve bit düzeyinde operatörlerden daha önceliklidir.

- Tüm karşılaştırma işleçleri eşit önceliğe sahiptir ve tümü mantıksal ve bit düzeyinde operatörlerden daha önceliklidir, ancak aritmetik ve birleştirme işleçlerinden daha düşük önceliğe sahiptir.

- Mantıksal ve bit düzeyinde işleçler aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümünün aritmetik, birleştirme ve karşılaştırma işleçlerinden daha düşük önceliği vardır.

- Eşit önceliğe sahip işleçler, ifadede göründükleri sırada soldan sağa değerlendirilir.

## <a name="precedence-order"></a>Öncelik sırası
 İşleçler aşağıdaki öncelik sırasına göre değerlendirilir:

### <a name="await-operator"></a>Await İşleci
 Await

### <a name="arithmetic-and-concatenation-operators"></a>Aritmetik ve birleştirme Işleçleri
 Üs (`^`)

 Birli kimlik ve olumsuzlama`+`( `–`,)

 Çarpma ve kayan nokta bölmesi (`*`,) `/`

 Tamsayı bölümü (`\`)

 Modüler aritmetik (`Mod`)

 Toplama ve çıkarma (`+`, `–`)

 Dize birleştirme (`&`)

 Aritmetik bit kaydırma (`<<`, `>>`)

### <a name="comparison-operators"></a>Karşılaştırma İşleçleri
 Tüm karşılaştırma işleçleri (`=`, `<>`, `<` `<=`,, `>`, ,,`Is`,, .`TypeOf`.. `IsNot` `>=` `Like` `Is`)

### <a name="logical-and-bitwise-operators"></a>Mantıksal ve Bit Düzeyinde İşleçler
 Değilleme`Not`()

 Birlikte (`And`, `AndAlso`)

 Kapsamlı ayırıcı (`Or`, `OrElse`)

 Dışlamalı ayırıcı (`Xor`)

### <a name="comments"></a>Açıklamalar
 `=` İşleci atama işleci değil yalnızca eşitlik karşılaştırma işleçtir.

 Dize birleştirme işleci (`&`) bir aritmetik işleç değil, ancak önceliğe göre Aritmetik işleçlerle gruplandırılır.

 `Is` Ve`IsNot` işleçleri nesne başvurusu karşılaştırma işleçleridir. İki nesnenin değerlerini karşılaştırmazlar; yalnızca iki nesne değişkeninin aynı nesne örneğine başvurmadığını belirlemesini denetler.

## <a name="associativity"></a>İlişkilendirilebilirlik
 Eşit önceliğe sahip işleçler bir ifadede birlikte görüntülendiğinde, örneğin çarpma ve bölme gibi, derleyici, her işlemi soldan sağa karşılaştığı şekilde değerlendirir. Aşağıdaki örnek bunu göstermektedir.

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 İlk ifade, Bölüm 96/8 ' i (12 ' de sonuç olarak) değerlendirir ve sonra Bölüm 12/4 ' dir ve bu da üç ile sonuçlanır. Derleyici işlemleri `n1` soldan sağa değerlendirdiği için, bu sıra için `n2`açıkça belirtildiği zaman değerlendirme aynı olur. Her `n1` ikisi `n2` de üç ile oluşur. Bunun aksine `n3` 48 sonucu vardır, çünkü parantezler derleyicinin önce 8/4 ' i değerlendirmesini zorlar.

 Bu davranış nedeniyle, operatörlerin Visual Basic olarak *sola ilişkilendirilebilir* olduğu söylenir.

## <a name="overriding-precedence-and-associativity"></a>Öncelik ve birleşim özelliklerini geçersiz kılma
 Bir ifadenin bazı bölümlerinin diğerlerinden önce değerlendirilmesini zorlamak için parantezleri kullanabilirsiniz. Bu, hem öncelik sırasını hem de sola ilişkilendirilebilirliği geçersiz kılabilir. Visual Basic, dış öğelerden önce parantez içine alınmış işlemleri her zaman gerçekleştirir. Bununla birlikte, parantez içinde parantez kullanmadığınız müddetçe, parantez içinde normal öncelik ve ilişkilendirilebilirlik sağlar. Aşağıdaki örnek bunu göstermektedir.

```vb
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
