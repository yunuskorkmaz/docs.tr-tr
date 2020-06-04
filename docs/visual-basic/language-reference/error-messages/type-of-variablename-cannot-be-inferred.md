---
title: Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '<variablename>' türü çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 74b690ce3dee87e481c629a254e629be4b40f8cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387016"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '\<variablename>' türü çıkarılamıyor

`For...Next`Aşağıdaki koşullar doğru olduğu için derleyicinin döngü denetim değişkeni için bir veri türünü çıkarmadığı bir döngü yazmadınız:

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

**Hata kimliği:** BC30982

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Döngü sınırlarının ve adım değişkeninin türlerini, en az birinin diğerlerinin genişlecekleri bir tür olması için gereken şekilde değiştirin. Yukarıdaki örnekte, türünü `stepVar` olarak değiştirin `Integer` .

  ```vb
  Dim stepVar = 1
  ```

  -veya-

  ```vb
  Dim stepVar As Integer = 1
  ```

- Döngü sınırlarını ve adım değişkenini uygun türlere dönüştürmek için açık dönüştürme işlevlerini kullanın. Yukarıdaki örnekte, `Val` işlevini öğesine uygulayın `stepVar` .

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next Deyimi](../statements/for-next-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer Deyimi](../statements/option-infer-statement.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
