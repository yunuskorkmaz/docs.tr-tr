---
title: "ULong Veri Türü (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ulong
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afc52bfd16541feed599d5445adad7aba04f8e9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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

Sayısal değişmez değerleri de dahil edebilirsiniz `UL` veya `ul` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `ULong` aşağıdaki örnekte gösterildiği gibi veri türü.

```vb
Dim number = &H00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Programlama ipuçları
  
-   **Negatif sayılar.** Çünkü `ULong` imzasız bir tür negatif bir sayı temsil edilemez. Tekli eksi kullanıyorsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `ULong`, Visual Basic ifade dönüştürür `Decimal` ilk.  
  
-   **CLS uyumluluğu.** `ULong` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), CLS uyumlu kod kullandığı bir bileşen kullanamayacaklarını şekilde.  
  
-   **Birlikte çalışma hakkında dikkat edilecek noktalar** Örnek otomasyon veya COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim varsa gibi türleri göz önünde bulundurmanız `ulong` farklı veri genişliği (32 bit) diğer ortamlarda olabilir. Bu tür bir bileşen için 32-bit bağımsız değişkeni geçirilirse olarak bildirme `UInteger` yerine `ULong` Yönetilen Visual Basic kod.  
  
     Ayrıca, Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde Otomasyon 64-bit tamsayı desteklemez. Visual Basic geçiremezsiniz `ULong` bir Otomasyon bileşen bu platformlarda bağımsız değişkeni.  
  
-   **Genişletme.** `ULong` Veri türü widens için `Decimal`, `Single`, ve `Double`. Bu dönüştürebilirsiniz anlamına gelir `ULong` karşılaşmadan olmadan bu türdeki herhangi bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakterleri ekleme `UL` bir hazır değer zorlar `ULong` veri türü. `ULong`hiçbir tanımlayıcı türü karakteri var.
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.UInt64>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Nasıl yapılır: imzalanmamış türler isteyen bir Windows işlevi çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
