---
title: '- İşleç (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 5f6b6b67e2999d380cfca078a43162b3e1db2206
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701298"
---
# <a name="--operator-visual-basic"></a>- İşleci (Visual Basic)
İki sayısal ifade arasındaki farkı ya da sayısal bir ifadenin negatif değerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
expression1 – expression2
```
  
veya

```vb  
–expression1  
```  
  
## <a name="parts"></a>Bölümler  
 `expression1`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `expression2`  
 @No__t-0 işleci negatif bir değer hesaplanmadığı için gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="result"></a>Sonuç  
 Sonuç, `expression1` ile `expression2` arasındaki fark veya `expression1` ' nin Değillenmiş değeri.  
  
 Sonuç veri türü, `expression1` ve `expression2` veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.  
  
## <a name="supported-types"></a>Desteklenen türler  
 Tüm sayısal türler. Bu, işaretsiz ve kayan nokta türlerini ve `Decimal` ' ı içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Daha önce gösterilen sözdiziminde gösterilen ilk kullanımda, `–` işleci iki sayısal ifade arasındaki fark için *ikili* aritmetik çıkarma işleçtir.  
  
 Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımda, `–` işleci bir ifadenin negatif değeri için *birli* olumsuzlama işleçidir. Bu anlamda, Olumsuzlaştırma `expression1` ' ın işaretini tersine döndürdükten sonra, `expression1` negatifse sonuç pozitif olur.  
  
 Her iki ifade de [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, `–` işleci onu sıfır olarak değerlendirir.  
  
> [!NOTE]
> @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayı arasındaki farkı hesaplamak ve döndürmek için `–` işlecini, sonra da bir sayıyı bir sayı olarak döndürür.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 @No__t-0, bu deyimlerin yürütülmesini takip eden 124,45 ve `unaryResult` içerir – 334,90 içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
