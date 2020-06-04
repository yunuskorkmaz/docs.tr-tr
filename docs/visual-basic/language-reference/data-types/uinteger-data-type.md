---
title: UInteger Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: 11070f6c7f3259b8c34528eb54d99b031b68f9f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415550"
---
# <a name="uinteger-data-type"></a>UInteger veri türü

0 ile 4.294.967.295 arasında değer değişen işaretsiz 32 bitlik (4 baytlık) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

`UInteger`Veri türü en etkili veri genişliğinde en büyük işaretsiz değeri sağlar.

Varsayılan değeri 0 ' `UInteger` dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `UInteger` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz. Tamsayı sabit değeri aralığın dışındaysa `UInteger` (diğer bir deyişle, değerinden küçükse <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt32.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 3.000.000.000 'e eşit tamsayılar `UInteger` değerlere atanır.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, `UI` `ui` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `UInteger` .

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Programlama ipuçları

`UInteger`Ve `Integer` veri türleri, daha küçük tamsayı türleri ( `UShort` , `Short` , ve), daha `Byte` `SByte` az bit kullansa bile, yükleme, depolama ve getirme için daha fazla zaman alan bir 32 bitlik işlemcide en iyi performansı sağlar.

- **Negatif sayılar.** `UInteger`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. `-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `UInteger` , Visual Basic ifadeyi `Long` önce dönüştürür.

- **CLS uyumluluğu.** `UInteger`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabirimleriniz varsa, gibi türlerin `uint` diğer ortamlarda farklı bir veri genişliğine (16 bit) sahip olabileceğini göz önünde bulundurun. Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu `UShort` `UInteger` yönetilen Visual Basic kodunuzda değil olarak bildirin.

- **Kan.** `UInteger`Veri türü,,,, ve için widens `Long` `ULong` `Decimal` `Single` `Double` . Bu, `UInteger` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .

- **Tür karakterleri.** Değişmez değer türü karakterlerinin `UI` bir sabit değere eklenmesi, `UInteger` veri türüne zorlar. `UInteger`tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.UInt32?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt32>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
