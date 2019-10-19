---
title: SByte Veri Türü (Visual Basic)
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
ms.openlocfilehash: a962200195002858257b92e92e0dd1383d4fb2d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582513"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte veri türü (Visual Basic)

-128 ile 127 arasında bir değer olan işaretli 8 bit (1 baytlık) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

@No__t_1 tam veri genişliğine veya `Short` yarı veri genişliğine gerek gerektirmeyen tamsayı değerleri içermesi için `SByte` veri türünü kullanın. Bazı durumlarda, ortak dil çalışma zamanı `SByte` değişkenlerinizi birbirine yakından paketlenebilir ve bellek tüketimini kaydedebilir.

@No__t_0 varsayılan değeri 0 ' dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `SByte` değişkeni bir ondalık sabit değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen-102 ' e eşit tamsayılar `SByte` değerlere atanır. Bu örnek, `/removeintchecks` derleyici anahtarıyla derlemeniz gerekir.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_` alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Tamsayı sabit değeri `SByte` aralığının dışındaysa (yani, <xref:System.SByte.MinValue?displayProperty=nameWithType> veya <xref:System.SByte.MaxValue?displayProperty=nameWithType> değerinden daha küçükse, bir derleme hatası oluşur. Bir tamsayı değişmez değeri hiç sonekine sahip olmadığında, bir [tamsayı](integer-data-type.md) çıkarsanın. Tamsayı sabit değeri `Integer` türü aralığının dışındaysa [Long](long-data-type.md) değeri algılanır. Yani, önceki örneklerde `0x9A` ve `0b10011010` sayısal değişmez değerler 156 değerine sahip 32 bitlik işaretli tamsayılar olarak yorumlanır ve bu da <xref:System.SByte.MaxValue?displayProperty=nameWithType> değerini aşar. Bir `SByte` ondalık olmayan bir tamsayı atayan bu gibi bir kodu başarıyla derlemek için aşağıdakilerden birini yapabilirsiniz:

- @No__t_0 derleyici anahtarıyla derleme yaparak tamsayı sınırları denetimlerini devre dışı bırakın.

- @No__t_1 atamak istediğiniz sabit değeri açıkça tanımlamak için bir [tür karakteri](../../programming-guide/language-features/data-types/type-characters.md) kullanın. Aşağıdaki örnek bir `SByte` negatif değişmez değer `Short` değeri atar. Negatif sayılar için, sayısal sabit değerin yüksek sıralı sözcüğünün yüksek sıralı bitinin ayarlanmış olması gerektiğini unutmayın. Örneğimizde bu, sabit değer `Short` değerinin 15 bit değeridir.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Programlama ipuçları

- **CLS uyumluluğu.** @No__t_0 veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.

- **Kan.** @No__t_0 veri türü `Short`, `Integer`, `Long`, `Decimal`, `Single` ve `Double` için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `SByte` bu türlerden birine dönüştürebileceğiniz anlamına gelir.

- **Tür karakterleri.** `SByte` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.SByte?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SByte?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
