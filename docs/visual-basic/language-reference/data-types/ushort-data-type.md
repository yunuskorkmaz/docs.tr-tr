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
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343862"
---
# <a name="ushort-data-type-visual-basic"></a>UShort veri türü (Visual Basic)

0 ile 65.535 arasında değer değişen işaretsiz 16 bit (2 baytlık) tamsayılar barındırır.  
  
## <a name="remarks"></a>Açıklamalar

 `Byte`için çok büyük olan ikili verileri içeren `UShort` veri türünü kullanın.  
  
 `UShort` varsayılan değeri 0 ' dır.  

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `UShort` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz. Tamsayı sabit değeri `UShort` aralığının dışındaysa (yani, <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya <xref:System.UInt16.MaxValue?displayProperty=nameWithType>değerinden daha küçükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 65.034 'e eşit tamsayılar `UShort` değerlere atanır.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `UShort` veri türünü belirtmek için `US` ya da `us` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Programlama ipuçları
  
- **Negatif sayılar.** `UShort` işaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. `UShort`türü değerlendirilen bir ifadede birli eksi (`-`) işlecini kullanırsanız, Visual Basic ifadeyi önce `Integer` dönüştürür.  
  
- **CLS uyumluluğu.** `UShort` veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.
  
- **Kan.** `UShort` veri türü `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`ve `Double`için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `UShort` bu türlerden birine dönüştürebileceğiniz anlamına gelir.  
  
- **Tür karakterleri.** Değişmez değer türü karakterlerinin bir hazır `US` eklenmesi, `UShort` veri türüne zorlar. `UShort` tanımlayıcı türü karakteri yok.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.UInt16?displayProperty=nameWithType> yapısıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt16>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
