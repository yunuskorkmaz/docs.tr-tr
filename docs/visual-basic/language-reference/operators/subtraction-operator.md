---
title: '- Operatör'
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
ms.openlocfilehash: b5129c2dbb361940fa6da2cb424ee23736ba72c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875326"
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
 Gereklidir. Herhangi bir sayısal ifade.  
  
 `expression2`  
 `–`İşleç negatif bir değer hesaplanmadığı için gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="result"></a>Sonuç  

 Sonuç, `expression1` ile veya arasında bir değer arasındaki farktır `expression2` `expression1` .  
  
 Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` . [Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.  
  
## <a name="supported-types"></a>Desteklenen türler  

 Tüm sayısal türler. Bu, imzasız ve kayan nokta türlerini içerir `Decimal` .  
  
## <a name="remarks"></a>Açıklamalar  

 Daha önce gösterilen sözdiziminde gösterilen ilk kullanımlarda `–` işleç, iki sayısal ifade arasındaki fark için *ikili* aritmetik çıkarma işleçidir.  
  
 Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımda `–` işleci, bir ifadenin negatif değeri için *birli* olumsuzlama işleçidir. Bu anlamda olumsuzlama, negatif ise sonucun pozitif olması için işaretini tersine döndürdükten oluşur `expression1` `expression1` .  
  
 Her iki ifade de [Nothing](../nothing.md)olarak değerlendirilirse, `–` işleç onu sıfır olarak değerlendirir.  
  
> [!NOTE]
> `–`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `–` iki sayı arasındaki farkı hesaplamak ve döndürmek için işlecini ve sonra bir sayıyı bir sayı olarak döndürür.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Bu deyimlerin yürütülmesi sonrasında `binaryResult` 124,45 ve `unaryResult` içerir – 334,90 içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-= İşleci (Visual Basic)](subtraction-assignment-operator.md)
- [Aritmetik Işleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
