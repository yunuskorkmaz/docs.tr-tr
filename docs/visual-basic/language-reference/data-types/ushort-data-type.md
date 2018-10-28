---
title: UShort Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
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
ms.openlocfilehash: 25ac46217a09d658ceaf92a8ea586259668314c1
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50040900"
---
# <a name="ushort-data-type-visual-basic"></a>UShort veri türü (Visual Basic)

(Değeri 0 ile 65.535 arasında değişen ayrı tutma imzasız 16-bit 2-bayt) tamsayıları.  
  
## <a name="remarks"></a>Açıklamalar

 Kullanım `UShort` veri türü için çok büyük ikili veri içermesini `Byte`.  
  
 Varsayılan değer olan `UShort` 0'dır.  

# <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirmek ve başlatmak bir `UShort` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren). Tamsayı sabit değeri aralığının dışında ise `UShort` (diğer bir deyişle, bu ise kısa <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 65,034 eşit ve ikili sabit değerler atanır `UShort` değerleri.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `US` veya `us` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `UShort` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Programlama ipuçları
  
-   **Negatif sayılar.** Çünkü `UShort` işaretsiz bir türü, negatif bir sayıyı temsil edemez. Tek işlenenli eksi işareti kullanırsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `UShort`, Visual Basic ifade dönüştürür `Integer` ilk.  
  
-   **CLS uyumluluğu.** `UShort` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), böylece onu kullanan bileşen CLS uyumlu kod kullanamıyor.
  
-   **Genişletme.** `UShort` Widens veri türü için `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ve `Double`. Yani dönüştürebilirsiniz `UShort` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Tür karakterleri.** Değişmez değer türü karakterleri ekleme `US` sabit değerine zorlar `UShort` veri türü. `UShort` hiçbir tanımlayıcı türü karakteri var.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.UInt16?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.UInt16>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
