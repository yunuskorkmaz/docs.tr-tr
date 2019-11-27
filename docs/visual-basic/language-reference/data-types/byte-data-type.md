---
title: Byte Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344074"
---
# <a name="byte-data-type-visual-basic"></a>Byte veri türü (Visual Basic)

0 ile 255 arasında değer aralığı olan işaretsiz 8 bit (1 baytlık) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

İkili veri içeren `Byte` veri türünü kullanın.  
  
`Byte` varsayılan değeri 0 ' dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `Byte` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz. İntegral sabit değeri bir `Byte` aralığının dışındaysa (yani, <xref:System.Byte.MinValue?displayProperty=nameWithType> veya <xref:System.Byte.MaxValue?displayProperty=nameWithType>değerinden daha büyükse) bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili harfler olarak temsil edilen 201 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `byte` değerlere dönüştürülür.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Örneğin:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Programlama ipuçları

- **Negatif sayılar.** `Byte` işaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. `Byte`türü değerlendirilen bir ifadede birli eksi (`-`) işlecini kullanırsanız, Visual Basic ifadeyi önce `Short` dönüştürür.
  
- **Biçim dönüştürmeleri.** Visual Basic dosyaları okurken veya yazarken ya da dll 'Leri, yöntemleri ve özellikleri çağırdığında, veri biçimleri arasında otomatik olarak dönüştürme yapılabilir. `Byte` değişkenleri ve dizileri içinde depolanan ikili veriler, bu tür biçim dönüştürmeleri sırasında korunur. İkili veriler için bir `String` değişkeni kullanmamalısınız, çünkü içeriği ANSI ve Unicode biçimleri arasında dönüştürme sırasında bozulabilir.

- **Kan.** `Byte` veri türü `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`veya `Double`için. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Byte` bu türlerden birine dönüştürebileceğiniz anlamına gelir.
  
- **Tür karakterleri.** `Byte` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Byte?displayProperty=nameWithType> yapısıdır.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, `b` bir `Byte` değişkenidir. Deyimleri, değişkeninin aralığını ve bit kaydırma operatörlerinin uygulamanın bir uygulamasını gösterir.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Byte?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
