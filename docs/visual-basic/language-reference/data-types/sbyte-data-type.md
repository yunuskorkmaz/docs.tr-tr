---
title: SByte Veri Türü
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415576"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte veri türü (Visual Basic)

-128 ile 127 arasında bir değer olan işaretli 8 bit (1 baytlık) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

`SByte`Veri türünü, tam veri genişliğinin `Integer` veya hatta yarı veri genişliğinin gerekli olmadığı tamsayı değerler içerecek şekilde kullanın `Short` . Bazı durumlarda, ortak dil çalışma zamanı `SByte` değişkenlerinizi birbirine yakından paketlenebilir ve bellek tüketimini kaydedebilir.

Varsayılan değeri 0 ' `SByte` dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `SByte` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen-102 arasındaki tamsayılar `SByte` değerlere atanır. Bu örnek, `/removeintchecks` derleyici anahtarıyla derlemeniz gerekir.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Tamsayı sabit değeri aralığın dışındaysa `SByte` (diğer bir deyişle, değerinden küçükse <xref:System.SByte.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.SByte.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur. Bir tamsayı değişmez değeri hiç sonekine sahip olmadığında, bir [tamsayı](integer-data-type.md) çıkarsanın. Tamsayı sabit değeri tür aralığının dışındaysa `Integer` , [uzun](long-data-type.md) bir değer algılanır. Diğer bir deyişle, önceki örneklerde sayısal değişmez değerler `0x9A` ve `0b10011010` 156 değeri olan 32 bitlik işaretli tamsayılar olarak yorumlanmaktadır <xref:System.SByte.MaxValue?displayProperty=nameWithType> . Öğesine ondalık olmayan bir tamsayı atayan bu gibi bir kodu başarıyla derlemek için aşağıdakilerden birini yapabilirsiniz `SByte` :

- Derleyici anahtarıyla derleme yaparak tamsayı sınırları denetimlerini devre dışı bırakın `/removeintchecks` .

- Öğesine atamak istediğiniz sabit değeri açıkça tanımlamak için bir [tür karakteri](../../programming-guide/language-features/data-types/type-characters.md) kullanın `SByte` . Aşağıdaki örnek bir için negatif bir değişmez `Short` değer atar `SByte` . Negatif sayılar için, sayısal sabit değerin yüksek sıralı sözcüğünün yüksek sıralı bitinin ayarlanmış olması gerektiğini unutmayın. Örneğimizde, bu değer değişmez değerin 15 ' i olur `Short` .

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Programlama ipuçları

- **CLS uyumluluğu.** `SByte`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.

- **Kan.** `SByte`Veri türü widens,,,, `Short` `Integer` `Long` `Decimal` `Single` , ve `Double` . Bu, `SByte` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .

- **Tür karakterleri.** `SByte`değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.SByte?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SByte?displayProperty=nameWithType>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Short Veri Türü](short-data-type.md)
- [Integer Veri Türü](integer-data-type.md)
- [Long Veri Türü](long-data-type.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
