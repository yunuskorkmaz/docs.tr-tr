---
title: Short Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343931"
---
# <a name="short-data-type-visual-basic"></a>Short veri türü (Visual Basic)

,-32.768 ile 32.767 arasında bir değere kadar olan işaretli 16 bit (2 baytlık) tamsayıları tutar.  
  
## <a name="remarks"></a>Açıklamalar  

 `Integer`tam veri genişliğini gerektirmeyen tamsayı değerleri içermesi için `Short` veri türünü kullanın. Bazı durumlarda, ortak dil çalışma zamanı `Short` değişkenlerinizi birbirine yakından paketedebilir ve bellek tüketimini kaydedebilir.  
  
 `Short` varsayılan değeri 0 ' dır.  
  
## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `Short` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz. Tamsayı sabit değeri `Short` aralığının dışındaysa (yani, <xref:System.Int16.MinValue?displayProperty=nameWithType> veya <xref:System.Int16.MaxValue?displayProperty=nameWithType>değerinden daha küçükse, bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili harfler olarak temsil edilen 1.034 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `Short` değerlere dönüştürülür.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `Short` veri türünü belirtmek için `S` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Kan.** `Short` veri türü `Integer`, `Long`, `Decimal`, `Single`veya `Double`için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Short` bu türlerden birine dönüştürebileceğiniz anlamına gelir.  
  
- **Tür karakterleri.** Değişmez değer türü karakter `S` bir sabit değere eklenmesi, `Short` veri türüne zorlar. `Short` tanımlayıcı türü karakteri yok.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int16?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
