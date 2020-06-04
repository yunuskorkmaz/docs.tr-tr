---
title: UShort Veri Türü
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
ms.openlocfilehash: ee31156e00059699125fd72a7f091afbb21beab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415485"
---
# <a name="ushort-data-type-visual-basic"></a>UShort veri türü (Visual Basic)

0 ile 65.535 arasında değer değişen işaretsiz 16 bit (2 baytlık) tamsayılar barındırır.  
  
## <a name="remarks"></a>Açıklamalar

 `UShort`İçin çok büyük ikili verileri içeren veri türünü kullanın `Byte` .  
  
 Varsayılan değeri 0 ' `UShort` dır.  

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `UShort` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz. Tamsayı sabit değeri aralığın dışındaysa `UShort` (diğer bir deyişle, değerinden küçükse <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt16.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 65.034 'e eşit tamsayılar `UShort` değerlere atanır.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, `US` `us` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `UShort` .

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Programlama ipuçları
  
- **Negatif sayılar.** `UShort`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. `-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `UShort` , Visual Basic ifadeyi `Integer` önce dönüştürür.  
  
- **CLS uyumluluğu.** `UShort`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.
  
- **Kan.** Veri türü,,,,, `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` , ve `Double` için widens. Bu, `UShort` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .  
  
- **Tür karakterleri.** Değişmez değer türü karakterlerinin `US` bir sabit değere eklenmesi, `UShort` veri türüne zorlar. `UShort`tanımlayıcı türü karakteri yok.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.UInt16?displayProperty=nameWithType> yapısıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt16>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
