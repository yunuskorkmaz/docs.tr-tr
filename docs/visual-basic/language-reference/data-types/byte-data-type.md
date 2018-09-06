---
title: Byte Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b106005ff07f55e05ae66dba94041cd8b5c24bb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869376"
---
# <a name="byte-data-type-visual-basic"></a>Byte veri türü (Visual Basic)
Değeri 0 ile 255 arasında imzalanmamış 8-bit (1-bayt) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

Kullanım `Byte` ikili veri içermesini veri türü.  
  
Varsayılan değer olan `Byte` 0'dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bildirmek ve başlatmak bir `Byte` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren). Tamsayı sabit değeri aralığının dışında ise bir `Byte` (diğer bir deyişle, bu ise kısa <xref:System.Byte.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Byte.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 201 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [tamsayı](integer-data-type.md) için `byte` değerleri.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Programlama ipuçları

-   **Negatif sayılar.** Çünkü `Byte` işaretsiz bir türü, negatif bir sayıyı temsil edemez. Tek işlenenli eksi işareti kullanırsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `Byte`, Visual Basic ifade dönüştürür `Short` ilk.
  
-   **Biçim dönüştürme.** Visual Basic okur veya yazar dosyaları veya DLL'leri, yöntemleri ve özellikleri çağırdığında, otomatik olarak veri biçimleri arasında dönüştürme yapabilirsiniz. İkili verilerin depolanmasını `Byte` değişkenleri ve dizileri gibi bir biçim dönüştürmelerini sırasında korunur. Kullanmamalısınız bir `String` ikili veriler için değişken içerikleri biçimlerini ANSI ve Unicode arasında dönüştürme sırasında bozuk olduğundan.

-   **Genişletme.** `Byte` Widens veri türü için `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, veya `Double`. Yani dönüştürebilirsiniz `Byte` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.
  
-   **Tür karakterleri.** `Byte` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.

-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Byte?displayProperty=nameWithType> yapısı.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, `b` olduğu bir `Byte` değişkeni. Deyimlerini değişkenin aralık ve bit düzeyinde kaydırma işleçleri, uygulamayı gösterir.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Ayrıca Bkz.

 <xref:System.Byte?displayProperty=nameWithType>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
