---
title: UInteger Veri türü (Visual Basic)
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
ms.openlocfilehash: 1ae0cbd3a518bf863a3c57f50934837a486d2901
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583131"
---
# <a name="uinteger-data-type"></a>UInteger veri türü

0 ile 4.294.967.295 arasında değer değişen işaretsiz 32 bitlik (4 baytlık) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

@No__t_0 veri türü en etkili veri genişliğinde en büyük işaretsiz değeri sağlar.

@No__t_0 varsayılan değeri 0 ' dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `UInteger` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz. Tamsayı sabit değeri `UInteger` aralığının dışındaysa (yani, <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya <xref:System.UInt32.MaxValue?displayProperty=nameWithType> değerinden daha küçükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 3.000.000.000 'e eşit tamsayılar `UInteger` değerlere atanır.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_` alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `UInteger` veri türünü belirtmek için `UI` ya da `ui` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Programlama ipuçları

@No__t_0 ve `Integer` veri türleri, daha küçük tamsayı türleri (`UShort`, `Short`, `Byte` ve `SByte`), daha az sayıda bit kullansa bile, yükleme için daha fazla zaman alacak şekilde 32 bitlik bir işlemcide en iyi performansı sağlar. , depola ve getir.

- **Negatif sayılar.** @No__t_0 işaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. @No__t_1 türü değerlendirilen bir ifadede birli eksi (`-`) işlecini kullanırsanız, Visual Basic ifadeyi önce `Long` dönüştürür.

- **CLS uyumluluğu.** @No__t_0 veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, `uint` gibi türlerin diğer ortamlarda farklı bir veri genişliğine (16 bit) sahip olabileceğini aklınızda bulundurun. Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu yönetilen Visual Basic kodunuzda `UInteger` yerine `UShort` olarak bildirin.

- **Kan.** @No__t_0 veri türü `Long`, `ULong`, `Decimal`, `Single` ve `Double` için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `UInteger` bu türlerden birine dönüştürebileceğiniz anlamına gelir.

- **Tür karakterleri.** Değişmez değer türü karakterlerinin bir hazır `UI` eklenmesi, `UInteger` veri türüne zorlar. `UInteger` tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.UInt32?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt32>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
