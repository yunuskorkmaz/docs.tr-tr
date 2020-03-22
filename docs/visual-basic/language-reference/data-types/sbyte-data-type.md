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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400794"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte veri türü (Visual Basic)

-128 ile 127 arasında değişen imzalı 8 bit (1 bayt) tümseci tutar.

## <a name="remarks"></a>Açıklamalar

Tam `SByte` veri genişliği `Integer` ve hatta yarım veri genişliği gerektirmeyen tamsayı değerlerini içerecek şekilde veri türünü kullanın. `Short` Bazı durumlarda, ortak dil çalışma süresi değişkenlerinizi `SByte` birbirine yakın bir şekilde paketleyebilir ve bellek tüketiminden tasarruf edebilir.

Varsayılan değeri `SByte` 0'dır.

## <a name="literal-assignments"></a>Gerçek atamalar

Bir `SByte` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.

Aşağıdaki örnekte, ondalık, hexadecimal ve ikili literals olarak temsil edilen -102'ye `SByte` eşit tamsayılar değerlere atanır. Bu örnek, `/removeintchecks` derleyici anahtarı yla derlemenizi gerektirir.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Tamsayı literal aralığının `SByte` dışında ysa (yani, daha az <xref:System.SByte.MinValue?displayProperty=nameWithType> veya daha <xref:System.SByte.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur. Bir sondanın sonek yoksa, bir [Integer](integer-data-type.md) çıkarılır. Tamsayı literal `Integer` türünün aralığının dışındaysa, [Uzun](long-data-type.md) çıkarılır. Bu, önceki örneklerde, sayısal literals `0x9A` ve `0b10011010` 32-bit imzalı tamsayılar 156 değerini aşan, aşan olarak yorumlanır anlamına gelir. <xref:System.SByte.MaxValue?displayProperty=nameWithType> Ondalık olmayan bir tamsayıyı bir `SByte`nesle atayan bu gibi kodu başarılı bir şekilde derlemek için aşağıdakilerden birini yapabilirsiniz:

- `/removeintchecks` Derleme anahtarıyla derleyerek, tümsesayı sınır denetimlerini devre dışı.

- 'ye atamak istediğiniz gerçek değeri açıkça tanımlamak için bir tür karakteri kullanın [type character](../../programming-guide/language-features/data-types/type-characters.md) `SByte` Aşağıdaki örnek, negatif bir `Short` edebi değer `SByte`atar. Negatif sayılar için sayısal kelimenin yüksek sıralı sözcüğünün yüksek sıralı bitinin ayarlanılması gerektiğini unutmayın. Örneğimizde, bu gerçek `Short` değerin bit 15'idir.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Programlama ipuçları

- **CLS Uyumluluğu.** Veri `SByte` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.

- **Genişletme.** Veri `SByte` `Short`türü , , `Integer`, `Long` `Decimal` `Single`, ve `Double`. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `SByte` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.

- **Karakterleri yazın.** `SByte`gerçek bir tür karakteri veya tanımlayıcı türü karakteri yoktur.

- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.SByte?displayProperty=nameWithType> tür yapıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SByte?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
