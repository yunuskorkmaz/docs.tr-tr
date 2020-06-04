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
ms.openlocfilehash: 7c076cd2198c85560f7c63c69e051697966c9524
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415602"
---
# <a name="long-data-type-visual-basic"></a>Long veri türü (Visual Basic)

-9223372036854775808 ile 9.223.372.036.854.775.807 (9.2... E + 18) değerinde değişen 64 bitlik (8 baytlık) tamsayıları barındırır.

## <a name="remarks"></a>Açıklamalar

Veri türüne `Long` sığmayacak kadar büyük olan tamsayı sayılarını içermesi için veri türünü kullanın `Integer` .

Varsayılan değeri 0 ' `Long` dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `Long` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz. Tamsayı sabit değeri aralığın dışındaysa `Long` (diğer bir deyişle, değerinden küçükse <xref:System.Int64.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.Int64.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 4.294.967.296 'e eşit tamsayılar `Long` değerlere atanır.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Long` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de tür karakterini içerebilir.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Birlikte çalışma konuları.** .NET Framework için yazılmayan bileşenlerle (örneğin, Otomasyon veya COM nesneleri) arabirimleriniz varsa, `Long` diğer ortamlarda farklı bir veri genişliğine (32 bit) sahip olduğunu unutmayın. Böyle bir bileşene 32 bitlik bir bağımsız değişken geçirıyorsanız, bunu `Integer` `Long` Yeni Visual Basic kodunuzda değil olarak bildirin.

- **Kan.** `Long`Veri türü widens, `Decimal` `Single` , veya `Double` . Bu, `Long` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .

- **Tür karakterleri.** Değişmez değer türü karakterini `L` bir sabit değere eklemek, `Long` veri türüne zorlar. Tanımlayıcı türü karakteri `&` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Long` .

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Int64?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int64>
- [Veri türleri](index.md)
- [Integer Veri Türü](integer-data-type.md)
- [Short Veri Türü](short-data-type.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
