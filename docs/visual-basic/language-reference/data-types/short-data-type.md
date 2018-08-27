---
title: Short Veri Türü (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: eb218a9b72208b13700ebd18dbf588066839203d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930158"
---
# <a name="short-data-type-visual-basic"></a>Short veri türü (Visual Basic)
-32.768 değeri ile 32.767 aralığı 16-bit (2-bayt) tamsayıları tutar imzalanmış.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Short` veri türü, tam veri genişliği gerektirmeyen tamsayı değerler içerecek şekilde `Integer`. Bazı durumlarda, ortak dil çalışma zamanı paketi, `Short` değişkenleri yakından birlikte ve bellek tüketimi.  
  
 Varsayılan değer olan `Short` 0'dır.  
  
## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirmek ve başlatmak bir `Short` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren). Tamsayı sabit değeri aralığının dışında ise `Short` (diğer bir deyişle, bu ise kısa <xref:System.Int16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int16.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 1,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [tamsayı](integer-data-type.md) için `Short` değerleri.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `S` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Short` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Programlama ipuçları

-   **Genişletme.** `Short` Widens veri türü için `Integer`, `Long`, `Decimal`, `Single`, veya `Double`. Yani dönüştürebilirsiniz `Short` karşılaşmadan bu türlerden herhangi birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Tür karakterleri.** Değişmez değer türü karakterinin `S` sabit değerine zorlar `Short` veri türü. `Short` hiçbir tanımlayıcı türü karakteri var.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Int16?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.Int16?displayProperty=nameWithType>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
