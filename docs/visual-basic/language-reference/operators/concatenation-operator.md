---
title: '&amp; İşleci'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336052"
---
# <a name="amp-operator-visual-basic"></a>&amp; Işleci (Visual Basic)
İki ifadenin dize birleştirmesini oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `String` veya `Object` değişken.  
  
 `expression1`  
 Gerekli. `String`bir veri türüne sahip herhangi bir ifade.  
  
 `expression2`  
 Gerekli. `String`bir veri türüne sahip herhangi bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `expression1` veya `expression2` veri türü `String` değilse ancak `String`için ise, `String`dönüştürülür. Veri türlerinden biri `String`olarak genişlemezse, derleyici bir hata oluşturur.  
  
 `result` veri türü `String`. Bir veya her iki ifade bir [Nothing](../../../visual-basic/language-reference/nothing.md) olarak değerlendirilir veya <xref:System.DBNull.Value?displayProperty=nameWithType>bir değere sahip olursa, "" değerine sahip bir dize olarak değerlendirilir.  
  
> [!NOTE]
> `&` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Ampersan (&) karakteri, değişkenleri tür `Long`olarak belirlemek için de kullanılabilir. Daha fazla bilgi için bkz. [tür karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, dize birleştirmesini zorlamak için `&` işlecini kullanır. Sonuç iki dize işleneninin birleştirilmesiyle temsil eden bir dize değeridir.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [&= İşleci](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic birleştirme Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
