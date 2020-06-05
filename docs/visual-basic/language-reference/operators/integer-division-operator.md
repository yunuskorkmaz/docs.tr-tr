---
title: '\ İşleci'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 1f8095afc5f096928b946607adc715af49827022
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370888"
---
# <a name="-operator-visual-basic"></a>\ İşleci (Visual Basic)
İki sayıyı böler ve bir tamsayı sonuç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `expression1`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
 `expression2`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İmzasız ve kayan nokta türleri de dahil olmak üzere tüm sayısal türler `Decimal` .  
  
## <a name="result"></a>Sonuç  
 Sonuç, `expression1` ' ın bölünen tamsayı `expression2` bölümüdür. Bu, kalanı atar ve yalnızca tamsayı kısmını korur. Bu, *kesme*olarak bilinir.  
  
 Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` . [Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.  
  
 [/İşleci (Visual Basic)](floating-point-division-operator.md) , kesir bölümünde kalanı tutan tam bölümü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bölme işlemini gerçekleştirmeden önce, Visual Basic herhangi bir kayan nokta sayısal ifadesini öğesine dönüştürmeye çalışır `Long` . `Option Strict`İse `On` , bir derleyici hatası oluşur. `Option Strict`İse `Off` , <xref:System.OverflowException> değer [uzun veri türü](../data-types/long-data-type.md)aralığının dışında ise mümkündür. Dönüşümü, `Long` *banker 'in yuvarlanması*için de tabidir. Daha fazla bilgi için [tür dönüştürme işlevlerinde](../functions/type-conversion-functions.md)"kesirli parçalar" bölümüne bakın.  
  
 `expression1`Ya da `expression2` [hiçbir şey](../nothing.md)değerlendirilirse, sıfır olarak değerlendirilir.  
  
## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  
 `expression2`Sıfır olarak değerlendirilirse, `\` işleci bir <xref:System.DivideByZeroException> özel durum atar. Bu, işlenenlerin tüm sayısal veri türleri için geçerlidir.  
  
> [!NOTE]
> `\`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `\` tam sayı bölümü yapmak için işlecini kullanır. Sonuç, geri kalan atılan iki işlenenin tamsayı bölümünü temsil eden bir tamsayıdır.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Yukarıdaki örnekteki ifadeler sırasıyla 2, 3, 33 ve-22 değerlerini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\\= İşleci](integer-division-assignment-operator.md)
- [/İşleci (Visual Basic)](floating-point-division-operator.md)
- [Option Strict Deyimi](../statements/option-strict-statement.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
