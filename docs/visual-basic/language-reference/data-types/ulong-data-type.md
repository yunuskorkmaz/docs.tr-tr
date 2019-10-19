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
ms.openlocfilehash: 19a75f056436b858a22588d7ac5f37df5dd326f2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583121"
---
# <a name="ulong-data-type-visual-basic"></a>ULong veri türü (Visual Basic)

0 ila 18446744073709551615 (1,84 ' den fazla 10 ^ 19 ' den fazla) değeri değişen işaretsiz 64 bitlik (8 baytlık) tamsayıları barındırır.

## <a name="remarks"></a>Açıklamalar

@No__t_1 için çok büyük olan ikili verileri veya en büyük olası işaretsiz tamsayı değerlerini içeren `ULong` veri türünü kullanın.

@No__t_0 varsayılan değeri 0 ' dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `ULong` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz. Tamsayı sabit değeri `ULong` aralığının dışındaysa (yani, <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya <xref:System.UInt64.MaxValue?displayProperty=nameWithType> değerinden daha küçükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 7.934.076.125 'e eşit tamsayılar `ULong` değerlere atanır.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_` alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `ULong` veri türünü belirtmek için `UL` ya da `ul` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Negatif sayılar.** @No__t_0 işaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. @No__t_1 türü değerlendirilen bir ifadede birli eksi (`-`) işlecini kullanırsanız, Visual Basic ifadeyi önce `Decimal` dönüştürür.

- **CLS uyumluluğu.** @No__t_0 veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, `ulong` gibi türlerin diğer ortamlarda farklı bir veri genişliğine (32 bit) sahip olabileceğini aklınızda bulundurun. Böyle bir bileşene 32 bitlik bir bağımsız değişken geçirıyorsanız, bunu yönetilen Visual Basic kodunuzda `ULong` yerine `UInteger` olarak bildirin.

  Ayrıca, Otomasyon Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde 64 bit tamsayıları desteklemez. Bu platformlarda bir Otomasyon bileşenine Visual Basic `ULong` bağımsız değişkeni geçiremezsiniz.

- **Kan.** @No__t_0 veri türü `Decimal`, `Single` ve `Double` için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `ULong` bu türlerden birine dönüştürebileceğiniz anlamına gelir.

- **Tür karakterleri.** Değişmez değer türü karakterlerinin bir hazır `UL` eklenmesi, `ULong` veri türüne zorlar. `ULong` tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt64>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
