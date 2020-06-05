---
title: Byte Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374323"
---
# <a name="byte-data-type-visual-basic"></a>Byte veri türü (Visual Basic)

0 ile 255 arasında değer aralığı olan işaretsiz 8 bit (1 baytlık) tamsayıları tutar.

## <a name="remarks"></a>Açıklamalar

`Byte`İkili veri içeren veri türünü kullanın.  
  
Varsayılan değeri 0 ' `Byte` dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `Byte` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz. İntegral sabit değeri bir ' nin aralığının dışındaysa `Byte` (yani, değerinden <xref:System.Byte.MinValue?displayProperty=nameWithType> büyük veya ondan büyükse <xref:System.Byte.MaxValue?displayProperty=nameWithType> ), bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 201 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `byte` değerlere dönüştürülür.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Programlama ipuçları

- **Negatif sayılar.** `Byte`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. `-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `Byte` , Visual Basic ifadeyi `Short` önce dönüştürür.
  
- **Biçim dönüştürmeleri.** Visual Basic dosyaları okurken veya yazarken ya da dll 'Leri, yöntemleri ve özellikleri çağırdığında, veri biçimleri arasında otomatik olarak dönüştürme yapılabilir. `Byte`Değişkenlerde ve dizilerde depolanan ikili veriler, bu tür biçim dönüştürmeleri sırasında korunur. `String`İkili veriler için bir değişken kullanmamalısınız, çünkü IÇERIĞI ANSI ve Unicode biçimleri arasında dönüştürme sırasında bozulmuş olabilir.

- **Kan.** `Byte`Veri türü widens,,,,, `Short` ,, `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` , veya `Double` . Bu, `Byte` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .
  
- **Tür karakterleri.** `Byte`değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Byte?displayProperty=nameWithType> yapısıdır.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, `b` bir `Byte` değişkendir. Deyimleri, değişkeninin aralığını ve bit kaydırma operatörlerinin uygulamanın bir uygulamasını gösterir.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Byte?displayProperty=nameWithType>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
