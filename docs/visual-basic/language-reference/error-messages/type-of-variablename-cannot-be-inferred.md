---
description: "Daha fazla bilgi: BC30982: ' ' türü, <variablename> döngü sınırları ve Step değişkeni aynı türe genişlemediğinden gösterilemiyor"
title: Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '<variablename>' türü çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 399e021500813127df6ecede2534783df09ac8dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641167"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>BC30982: ' ' türü, \<variablename> döngü sınırları ve Step değişkeni aynı türe genişlemediğinden çıkarsanamıyor

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
