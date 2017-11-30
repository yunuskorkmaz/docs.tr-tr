---
title: "UShort Veri Türü (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513e8ce4694788d33c5aa14e34b95e88b6d37ff1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-data-type-visual-basic"></a>UShort veri türü (Visual Basic)

Değer 0'dan 65.535 arasında değişen ayrı tutma işaretsiz 16-bit (2-bayt) tamsayı.  
  
## <a name="remarks"></a>Açıklamalar

 Kullanım `UShort` veri türü için çok büyük ikili verileri içerecek şekilde `Byte`.  
  
 Varsayılan değer olan `UShort` 0'dır.  

# <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirme ve başlatma bir `UShort` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak). Değişmez değer tamsayı aralığı dışında ise `UShort` (diğer bir deyişle, bu ise değerinden <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 65,034 tamsayılar eşit ve ikili değişmez değerler atanır `UShort` değerleri.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Sayısal değişmez değerleri de dahil edebilirsiniz `US` veya `us` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `UShort` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H035826us
```

## <a name="programming-tips"></a>Programlama ipuçları
  
-   **Negatif sayılar.** Çünkü `UShort` imzasız bir tür negatif bir sayı temsil edilemez. Tekli eksi kullanıyorsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `UShort`, Visual Basic ifade dönüştürür `Integer` ilk.  
  
-   **CLS uyumluluğu.** `UShort` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), CLS uyumlu kod kullandığı bir bileşen kullanamayacaklarını şekilde.
  
-   **Genişletme.** `UShort` Veri türü widens için `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ve `Double`. Bu dönüştürebilirsiniz anlamına gelir `UShort` karşılaşmadan olmadan bu türdeki herhangi bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakterleri ekleme `US` bir hazır değer zorlar `UShort` veri türü. `UShort`hiçbir tanımlayıcı türü karakteri var.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.UInt16?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.UInt16>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Nasıl yapılır: imzalanmamış türler isteyen bir Windows işlevi çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
