---
title: Long Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343971"
---
# <a name="long-data-type-visual-basic"></a>Long veri türü (Visual Basic)

-9223372036854775808 ile 9.223.372.036.854.775.807 (9.2... E + 18) değerinde değişen 64 bitlik (8 baytlık) tamsayıları barındırır.

## <a name="remarks"></a>Açıklamalar

`Integer` veri türüne sığamayacak kadar büyük tamsayı sayılar içermesi için `Long` veri türünü kullanın.

`Long` varsayılan değeri 0 ' dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `Long` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz. Tamsayı sabit değeri `Long` aralığının dışındaysa (yani, <xref:System.Int64.MinValue?displayProperty=nameWithType> veya <xref:System.Int64.MaxValue?displayProperty=nameWithType>değerinden daha küçükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 4.294.967.296 'e eşit tamsayılar `Long` değerlere atanır.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `Long` veri türünü belirtmek için `L` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Birlikte çalışma konuları.** .NET Framework için yazılmayan bileşenlerle (örneğin, Automation veya COM nesneleri) arabirimleriniz varsa, `Long` başka ortamlarda farklı bir veri genişliğine (32 bit) sahip olduğunu unutmayın. Böyle bir bileşene 32 bitlik bir bağımsız değişken geçirdiğinizden, bunu yeni Visual Basic kodunuzda `Long` yerine `Integer` olarak bildirin.

- **Kan.** `Long` veri türü `Decimal`, `Single`veya `Double`için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Long` bu türlerden birine dönüştürebileceğiniz anlamına gelir.

- **Tür karakterleri.** Değişmez değer türü karakter `L` bir sabit değere eklenmesi, `Long` veri türüne zorlar. Tanımlayıcı türü karakter `&` herhangi bir tanımlayıcıya eklemek bunu `Long`zorlar.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Int64?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int64>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
