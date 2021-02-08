---
description: ': İşleci hakkında daha fazla bilgi edinin &amp; (Visual Basic)'
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
ms.openlocfilehash: ba7c94805e805c841d05241fef557ca972a19ae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774102"
---
# <a name="amp-operator-visual-basic"></a>&amp; İşleç (Visual Basic)

İki ifadenin dize birleştirmesini oluşturur.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Bölümler  

 `result`  
 Gereklidir. Herhangi bir `String` veya `Object` değişken.  
  
 `expression1`  
 Gereklidir. Widens tarafından kullanılan bir veri türüne sahip herhangi bir ifade `String` .  
  
 `expression2`  
 Gereklidir. Widens tarafından kullanılan bir veri türüne sahip herhangi bir ifade `String` .  
  
## <a name="remarks"></a>Açıklamalar  

 Veya veri türü `expression1` `expression2` değilse `String` , ancak widens ise `String` , öğesine dönüştürülür `String` . Veri türlerinden biri olarak genişlemezse `String` , derleyici bir hata oluşturur.  
  
 Veri türü `result` `String` . Bir veya her iki ifade bir [Nothing](../nothing.md) olarak değerlendirilir veya bir değerine sahip olursa <xref:System.DBNull.Value?displayProperty=nameWithType> , "" değerine sahip bir dize olarak değerlendirilir.  
  
> [!NOTE]
> `&`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Ve (&) karakteri değişkenleri tür olarak tanımlamak için de kullanılabilir `Long` . Daha fazla bilgi için bkz. [tür karakterleri](../../programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Örnek  

 Bu örnek, `&` dize birleştirmesini zorlamak için işlecini kullanır. Sonuç iki dize işleneninin birleştirilmesiyle temsil eden bir dize değeridir.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [&= Işleci](and-assignment-operator.md)
- [Birleştirme İşleçleri](concatenation-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Birleştirme İşleçleri](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
