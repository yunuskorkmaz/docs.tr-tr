---
title: "Byte Veri Türü (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6475ff3ed905abb022a9ef60204c04b45130ae22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="byte-data-type-visual-basic"></a>Byte veri türü (Visual Basic)
Değeri 0 ile 255 arasında imzalanmamış 8 bit (1-bayt) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

Kullanım `Byte` veri türü ikili verileri içerir.  
  
Varsayılan değer olan `Byte` 0'dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirme ve başlatma bir `Byte` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak). Tam sayı sabit değeri aralığının dışında olması durumunda bir `Byte` (diğer bir deyişle, bu ise değerinden <xref:System.Byte.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Byte.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 201 tamsayılar eşit ve ikili değişmez değerleri gelen örtük olarak dönüştürülür [tamsayı](integer-data-type.md) için `byte` değerleri.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

## <a name="programming-tips"></a>Programlama ipuçları

-   **Negatif sayılar.** Çünkü `Byte` imzasız bir tür negatif bir sayı temsil edilemez. Tekli eksi kullanıyorsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `Byte`, Visual Basic ifade dönüştürür `Short` ilk.
  
-   **Biçim dönüşümler.** Visual Basic okur veya dosyaları yazma veya DLL'leri, yöntemleri ve özellikleri aradığında, veri biçimleri arasında otomatik olarak dönüştürebilir. Depolanan ikili veri `Byte` değişkenleri ve dizileri böyle formatı dönüştürme sırasında korunur. Kullanılamaz bir `String` ANSI veya Unicode biçimleri arasında dönüştürme sırasında içeriğinin bozuk için değişken ikili veriler için.

-   **Genişletme.** `Byte` Veri türü widens için `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, veya `Double`. Bu dönüştürebilirsiniz anlamına gelir `Byte` karşılaşmadan olmadan bu türdeki herhangi bir <xref:System.OverflowException?displayProperty=nameWithType> hata.
  
-   **Karakterleri yazın.** `Byte`değişmez değer türü karakteri ya da tanımlayıcı türü karakteri içeriyor.

-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Byte?displayProperty=nameWithType> yapısı.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, `b` olan bir `Byte` değişkeni. Aralık değişkeninin ve bit kaydırma işleçleri uygulama ona deyimleri gösterir.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Ayrıca Bkz.

 <xref:System.Byte?displayProperty=nameWithType>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
