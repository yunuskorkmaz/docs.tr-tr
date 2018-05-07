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
ms.openlocfilehash: 1b0137f0f33abfdb3f03758323edeaa63ac60117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ulong-data-type-visual-basic"></a>ULong veri türü (Visual Basic)

İşaretsiz 64-bit (8-bayt) tamsayı değeri 0'dan 18,446,744,073,709,551,615 arasında değişen tutar (1.84 kereden fazla 10 ^ 19).  
  
## <a name="remarks"></a>Açıklamalar

Kullanım `ULong` veri türü için çok büyük ikili verileri içerecek şekilde `UInteger`, veya en büyük olası imzasız tamsayı değerleri.  
  
Varsayılan değer olan `ULong` 0'dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirme ve başlatma bir `ULong` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak). Değişmez değer tamsayı aralığı dışında ise `ULong` (diğer bir deyişle, bu ise değerinden <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 7,934,076,125 tamsayılar eşit ve ikili değişmez değerler atanır `ULong` değerleri.
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak. Örneğin:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerleri de dahil edebilirsiniz `UL` veya `ul` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `ULong` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Programlama ipuçları
  
-   **Negatif sayılar.** Çünkü `ULong` imzasız bir tür negatif bir sayı temsil edilemez. Tekli eksi kullanıyorsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `ULong`, Visual Basic ifade dönüştürür `Decimal` ilk.  
  
-   **CLS uyumluluğu.** `ULong` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), CLS uyumlu kod kullandığı bir bileşen kullanamayacaklarını şekilde.  
  
-   **Birlikte çalışma hakkında dikkat edilecek noktalar** Örnek otomasyon veya COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim varsa gibi türleri göz önünde bulundurmanız `ulong` farklı veri genişliği (32 bit) diğer ortamlarda olabilir. Bu tür bir bileşen için 32-bit bağımsız değişkeni geçirilirse olarak bildirme `UInteger` yerine `ULong` Yönetilen Visual Basic kod.  
  
     Ayrıca, Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde Otomasyon 64-bit tamsayı desteklemez. Visual Basic geçiremezsiniz `ULong` bir Otomasyon bileşen bu platformlarda bağımsız değişkeni.  
  
-   **Genişletme.** `ULong` Veri türü widens için `Decimal`, `Single`, ve `Double`. Bu dönüştürebilirsiniz anlamına gelir `ULong` karşılaşmadan olmadan bu türdeki herhangi bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakterleri ekleme `UL` bir hazır değer zorlar `ULong` veri türü. `ULong` hiçbir tanımlayıcı türü karakteri var.
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.UInt64>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
