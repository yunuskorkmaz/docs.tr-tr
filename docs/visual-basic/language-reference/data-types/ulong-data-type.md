---
title: ULong Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214243f6a8a87f4e4cc15f31be23275fff00d07d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43797981"
---
# <a name="ulong-data-type-visual-basic"></a>ULong veri türü (Visual Basic)

Değeri 0'dan 18,446,744,073,709,551,615 arasında değişen işaretsiz 64-bit (8 bayt) tamsayıları tutar (1.84 kereden fazla 10 ^ 19).  
  
## <a name="remarks"></a>Açıklamalar

Kullanım `ULong` veri türü için çok büyük ikili veri içermesini `UInteger`, veya en büyük olası işaretsiz tamsayı değerleri.  
  
Varsayılan değer olan `ULong` 0'dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirmek ve başlatmak bir `ULong` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren). Tamsayı sabit değeri aralığının dışında ise `ULong` (diğer bir deyişle, bu ise kısa <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 7,934,076,125 eşit ve ikili sabit değerler atanır `ULong` değerleri.
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `UL` veya `ul` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `ULong` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Programlama ipuçları
  
-   **Negatif sayılar.** Çünkü `ULong` işaretsiz bir türü, negatif bir sayıyı temsil edemez. Tek işlenenli eksi işareti kullanırsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `ULong`, Visual Basic ifade dönüştürür `Decimal` ilk.  
  
-   **CLS uyumluluğu.** `ULong` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), böylece onu kullanan bileşen CLS uyumlu kod kullanamıyor.  
  
-   **Birlikte çalışabilirlik değerlendirmeleri.** Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, gibi türleri akılda tutulması `ulong` diğer ortamlarda farklı veri genişliği (32 bit) olabilir. Bir 32-bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `UInteger` yerine `ULong` Yönetilen Visual Basic kodunuzda.  
  
     Ayrıca, Windows 95, Windows 98, Windows ME veya Windows 2000 Otomasyon 64-bit tamsayıya desteklemez. Bir Visual Basic geçirilemez `ULong` bir Otomasyon bileşen bu platformlardaki bağımsız değişkeni.  
  
-   **Genişletme.** `ULong` Widens veri türü için `Decimal`, `Single`, ve `Double`. Yani dönüştürebilirsiniz `ULong` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Tür karakterleri.** Değişmez değer türü karakterleri ekleme `UL` sabit değerine zorlar `ULong` veri türü. `ULong` hiçbir tanımlayıcı türü karakteri var.
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.UInt64?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.UInt64>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
