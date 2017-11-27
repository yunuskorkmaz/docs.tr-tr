---
title: "Onluk Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a>Onluk Veri Türü (Visual Basic)
Ayrı tutma 128-bit (16 bayt) değerleri değişken gücünü 10 tarafından ölçeklendirilmiş 96-bit (12-bayt) tamsayı numaraları temsil eden imzalı. Ölçeklendirme faktörü ondalık basamak sayısını belirtir; 0 ile 28 arasında çeşitlilik gösterir. Ölçeği 0 (hiçbir ondalık basamak) ile en büyük olası 79,228,162,514,264,337,593,543,950,335 +/-değerdir (7 +/-.9228162514264337593543950335E + 28). 28 ondalık basamak, en büyük değeri +/-7.9228162514264337593543950335, ve sıfır olmayan en küçük değeri +/-0.0000000000000000000000000001 (+/-1E-28).  
  
## <a name="remarks"></a>Açıklamalar  
 `Decimal` Veri türü için bir sayı en önemli basamak sayısını sağlar. 29 önemli basamak destekler ve 7.9228 x 10 aşan değerleri temsil edebilir ^ 28. Gibi hesaplamaları için özellikle uygun finansal, çok sayıda basamak gerektirir ancak yuvarlama hataları tolerans olamaz.  
  
 Varsayılan değer olan `Decimal` 0'dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Hassasiyet.** `Decimal`kayan nokta veri türü değil. `Decimal` Yapısı tutan bir oturum bit ve ölçeklendirme hangi değer bir ondalık kesir bölümüdür belirtir çarpanı bir tamsayı ile birlikte bir ikili tamsayı değeri. Bu nedenle, `Decimal` numaraları kayan nokta türleri daha bellekte daha kesin bir gösterimi olan (`Single` ve `Double`).  
  
-   **Performans.** `Decimal` Veri türü olan tüm sayısal türler en yavaş. Bir veri türü işaretlemeden önce performans karşı duyarlılığı önemini tartmanız gerekir.  
  
-   **Genişletme.** `Decimal` Veri türü widens için `Single` veya `Double`. Bu dönüştürebilirsiniz anlamına gelir `Decimal` karşılaşmadan olmadan bu tür ya da bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Sondaki sıfırlar.** Visual Basic sıfırları saklamadığı bir `Decimal` değişmez. Ancak, bir `Decimal` değişkeni pkı'ya edinilen Sondaki sıfırları korur. Aşağıdaki örnek bunu göstermektedir.  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     Çıktısını `MsgBox` önceki örnekte aşağıdaki gibidir:  
  
     D1 2.375, d2 = 1.625, d3 = 4.000, d4 = 4 =  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ekleme `D` bir hazır değer zorlar `Decimal` veri türü. Tanımlayıcı türü karakteri ekleme `@` herhangi bir tanımlayıcı zorlar `Decimal`.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Decimal?displayProperty=nameWithType> yapısı.  
  
## <a name="range"></a>Aralık  
 Kullanmanız gerekebilir `D` türü büyük bir değere atamak için karakteri bir `Decimal` değişken veya sabit. Bu gereksinim derleyici sabit değer olarak yorumlar çünkü `Long` değişmez değer türü karakteri değişmez değeri aşağıdaki örnekte gösterildiği gibi aşağıdaki sürece.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 Bildirimi `bigDec1` kendisine atanmış değer aralığı içinde kaldığından taşma oluşturmuyor `Long`. `Long` Değer atanabilen `Decimal` değişkeni.  
  
 Bildirimi `bigDec2` kendisine atanmış değeri için çok büyük olduğundan taşma hatası oluşturur `Long`. Sayısal sabit değer olarak ilk yorumlanamayan çünkü bir `Long`, için atanamaz `Decimal` değişkeni.  
  
 İçin `bigDec3`, değişmez değer türü karakteri `D` sabit değer olarak yorumlamaya derleyici zorlayarak sorununu çözer bir `Decimal` yerine olarak bir `Long`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Single veri türü](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
