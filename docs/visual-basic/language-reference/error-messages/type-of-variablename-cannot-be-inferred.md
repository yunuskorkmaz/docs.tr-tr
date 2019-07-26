---
title: Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '<variablename>' türü çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512715"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Döngü sınırları ve\<Step değişkeni aynı türe genişlemediğinden ' VariableName > ' türü çıkarsanamıyor

Aşağıdaki koşullar doğru olduğu `For...Next` için derleyicinin döngü denetim değişkeni için bir veri türünü çıkarmadığı bir döngü yazmadınız:

- Döngü denetim değişkeninin veri türü bir `As` yan tümcesiyle belirtilmemiş.

- Döngü sınırları ve Step değişkeni en az iki veri türü içeriyor.

- Veri türleri arasında standart dönüştürmeler yok.

 Bu nedenle, derleyici bir döngünün denetim değişkeninin veri türünü çıkarsamaz.

 Aşağıdaki örnekte, Step değişkeni bir karakterdir ve döngü sınırlarının her ikisi de tamsayılardır. Karakterler ve tamsayılar arasında standart dönüştürme olmadığından, bu hata bildirilir.

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**Hata KIMLIĞI:** BC30982

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Döngü sınırlarının ve adım değişkeninin türlerini, en az birinin diğerlerinin genişlecekleri bir tür olması için gereken şekilde değiştirin. Yukarıdaki örnekte, türünü `stepVar` olarak `Integer`değiştirin.

  ```vb
  Dim stepVar = 1
  ```

  -veya-

  ```vb
  Dim stepVar As Integer = 1
  ```

- Döngü sınırlarını ve adım değişkenini uygun türlere dönüştürmek için açık dönüştürme işlevlerini kullanın. Yukarıdaki örnekte, `Val` işlevini öğesine `stepVar`uygulayın.

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
