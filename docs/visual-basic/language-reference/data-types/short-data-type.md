---
title: "Short Veri Türü (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords: vb.Short
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
ms.openlocfilehash: fef948debed69cf9fb7b0e6bb65eb0ddbe497a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="short-data-type-visual-basic"></a>Short veri türü (Visual Basic)
Ayrı tutma 32,768 değeri ile 32.767 aralığı 16-bit (2-bayt) tamsayılar imzalanmış.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Short` veri türü tam veri genişliği gerektirmeyen tamsayı değerleri içeren `Integer`. Bazı durumlarda, ortak dil çalışma zamanı paketi, `Short` değişkenleri yakın işbirliği içinde ve bellek tüketimi.  
  
 Varsayılan değer olan `Short` 0'dır.  
  
## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirme ve başlatma bir `Short` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak). Değişmez değer tamsayı aralığı dışında ise `Short` (diğer bir deyişle, bu ise değerinden <xref:System.Int16.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int16.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 1,034 tamsayılar eşit ve ikili değişmez değerleri gelen örtük olarak dönüştürülür [tamsayı](integer-data-type.md) için `Short` değerleri.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Sayısal değişmez değerleri de dahil edebilirsiniz `S` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Short` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H0326S
```

## <a name="programming-tips"></a>Programlama ipuçları

-   **Genişletme.** `Short` Veri türü widens için `Integer`, `Long`, `Decimal`, `Single`, veya `Double`. Bu dönüştürebilirsiniz anlamına gelir `Short` karşılaşmadan olmadan bu türlerinden herhangi biri için bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ekleme `S` bir hazır değer zorlar `Short` veri türü. `Short`hiçbir tanımlayıcı türü karakteri var.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.Int16?displayProperty=nameWithType>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Integer veri türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long veri türü](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
