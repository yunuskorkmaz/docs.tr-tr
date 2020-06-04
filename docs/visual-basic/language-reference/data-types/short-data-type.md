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
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415563"
---
# <a name="short-data-type-visual-basic"></a>Short veri türü (Visual Basic)

,-32.768 ile 32.767 arasında bir değere kadar olan işaretli 16 bit (2 baytlık) tamsayıları tutar.  
  
## <a name="remarks"></a>Açıklamalar  

 `Short`Veri türünü, tam veri genişliği gerektirmeyen tamsayı değerler içerecek şekilde kullanın `Integer` . Bazı durumlarda, ortak dil çalışma zamanı `Short` değişkenlerinizi birbirine yakından paketedebilir ve bellek tüketimini kaydedebilir.  
  
 Varsayılan değeri 0 ' `Short` dır.  
  
## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `Short` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz. Tamsayı sabit değeri aralığın dışındaysa `Short` (diğer bir deyişle, değerinden küçükse <xref:System.Int16.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.Int16.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 1.034 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `Short` değerlere dönüştürülür.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Short` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de tür karakterini içerebilir.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Kan.** `Short`Veri türü widens,,,, `Integer` `Long` `Decimal` `Single` veya `Double` . Bu, `Short` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .  
  
- **Tür karakterleri.** Değişmez değer türü karakterini `S` bir sabit değere eklemek, `Short` veri türüne zorlar. `Short`tanımlayıcı türü karakteri yok.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int16?displayProperty=nameWithType>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Integer Veri Türü](integer-data-type.md)
- [Long Veri Türü](long-data-type.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
