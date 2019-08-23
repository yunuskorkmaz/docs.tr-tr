---
title: '&amp;İşleç (Visual Basic)'
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
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968350"
---
# <a name="amp-operator-visual-basic"></a>&amp;İşleç (Visual Basic)
İki ifadenin dize birleştirmesini oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi `String` bir `Object` veya değişken.  
  
 `expression1`  
 Gerekli. Widens tarafından kullanılan bir veri türüne sahip herhangi bir `String`ifade.  
  
 `expression2`  
 Gerekli. Widens tarafından kullanılan bir veri türüne sahip herhangi bir `String`ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `expression1` `String` `String`Veya veri türü değilse`String` , ancak widens ise, öğesine dönüştürülür. `expression2` Veri türlerinden biri olarak `String`genişlemezse, derleyici bir hata oluşturur.  
  
 Veri türü `result`. `String` Bir veya her iki ifade bir [Nothing](../../../visual-basic/language-reference/nothing.md) olarak değerlendirilir veya bir değerine <xref:System.DBNull.Value?displayProperty=nameWithType>sahip olursa, "" değerine sahip bir dize olarak değerlendirilir.  
  
> [!NOTE]
> İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `&` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Ve (&) karakteri değişkenleri tür `Long`olarak tanımlamak için de kullanılabilir. Daha fazla bilgi için bkz. [tür karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, `&` dize birleştirmesini zorlamak için işlecini kullanır. Sonuç iki dize işleneninin birleştirilmesiyle temsil eden bir dize değeridir.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [&= İşleci](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic birleştirme Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
