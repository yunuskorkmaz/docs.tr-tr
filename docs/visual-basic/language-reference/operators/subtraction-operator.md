---
title: '- İşleç'
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
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348219"
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
 `–` işleci negatif bir değer hesaplanmadığı için gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="result"></a>Sonuç  
 Sonuç, `expression1` ve `expression2`ya da `expression1`'in nelenmiş değeri arasındaki farktır.  
  
 Sonuç veri türü, `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.  
  
## <a name="supported-types"></a>Desteklenen türler  
 Tüm sayısal türler. Bu, işaretsiz ve kayan nokta türlerini ve `Decimal`içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Daha önce gösterilen sözdiziminde gösterilen ilk kullanımlarda, `–` işleci iki sayısal ifade arasındaki fark için *ikili* aritmetik çıkarma işleçidir.  
  
 Daha önce gösterilen sözdiziminde gösterilen ikinci kullanım için `–` işleci, bir ifadenin negatif değeri için *birli* olumsuzlama işleçidir. Bu anlamda olumsuzlama, `expression1` negatifse, sonucun pozitif olması için `expression1` işaretini ters çevirmeyi içerir.  
  
 Her iki ifade de [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, `–` işleci onu sıfır olarak değerlendirir.  
  
> [!NOTE]
> `–` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki sayı arasındaki farkı hesaplamak ve döndürmek için `–` işlecini, sonra da bir sayıyı bir sayı olarak döndürür.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Bu deyimlerin yürütülmesini izleyerek `binaryResult` 124,45 ve `unaryResult` içerir – 334,90.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
