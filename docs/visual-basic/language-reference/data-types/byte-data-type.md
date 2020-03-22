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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400745"
---
# <a name="byte-data-type-visual-basic"></a>Bayt veri türü (Visual Basic)

0 ile 255 arasında değişen imzasız 8 bit (1 bayt) tümseci tutar.

## <a name="remarks"></a>Açıklamalar

İkili `Byte` verileri içerecek şekilde veri türünü kullanın.  
  
Varsayılan değeri `Byte` 0'dır.

## <a name="literal-assignments"></a>Gerçek atamalar

Bir `Byte` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz. Integral literal bir `Byte` aralığın dışında ise (yani, daha <xref:System.Byte.MinValue?displayProperty=nameWithType> az veya <xref:System.Byte.MaxValue?displayProperty=nameWithType>daha büyükse), bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, hexadecimal ve ikili literalolarak temsil edilen 201'e eşit tamsayılar dolaylı olarak `byte` [Tamsayı'dan](integer-data-type.md) değerlere dönüştürülür.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> `&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız. Ondalık edebi hiçbir önek var.

Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz. Örnek:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Programlama ipuçları

- **Negatif Sayılar.** İmzalanmamış bir tür `Byte` olduğundan, negatif bir sayıyı temsil edemez. Unary eksi (`-`) işleci, yazmayı `Byte`değerlendiren bir ifadeüzerinde kullanırsanız, `Short` Visual Basic ifadeyi önce dönüştürür.
  
- **Dönüşümleri Biçimlendirin.** Visual Basic dosyaları okuduğunda veya yazdığında veya DL'leri, yöntemleri ve özellikleri çağırdığında, veri biçimleri arasında otomatik olarak dönüştürebilir. Değişkenler ve `Byte` diziler halinde depolanan ikili veriler, bu biçim dönüştürmeleri sırasında korunur. İçeriği ANSI `String` ve Unicode biçimleri arasında dönüştürme sırasında bozulabileceğinden, ikili veriler için bir değişken kullanmamalısınız.

- **Genişletme.** Veri `Byte` `Short`türü `UShort`, , `Integer` `UInteger` `Long` `ULong`, , `Decimal`, `Single`, `Double`, veya . Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Byte` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.
  
- **Karakterleri yazın.** `Byte`gerçek bir tür karakteri veya tanımlayıcı türü karakteri yoktur.

- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.Byte?displayProperty=nameWithType> tür yapıdır.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, `b` bir `Byte` değişkendir. İfadeler değişkenin aralığını ve bit kaydırma işleçlerinin buna uygulanmasını gösterir.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Byte?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
