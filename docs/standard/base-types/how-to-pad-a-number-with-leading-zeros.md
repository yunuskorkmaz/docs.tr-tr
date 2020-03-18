---
title: 'Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma'
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131982"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma

"D" [standart sayısal biçim dizesini](../../../docs/standard/base-types/standard-numeric-format-strings.md) hassas bir belirtimle kullanarak bir tamsayıya satır aralığı sıfırları ekleyebilirsiniz. [Özel bir sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md)kullanarak hem tamsayı hem de kayan nokta numaralarına satır aralığı sıfırları ekleyebilirsiniz. Bu makalede, önde gelen sıfırlar ile bir sayı pad için her iki yöntem nasıl kullanılacağını gösterir.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Belirli bir uzunluğa giden sıfırları içeren bir tamsayıyı deftere

1. Tümsek değerinin görüntülenmesini istediğiniz en az basamak sayısını belirleyin. Bu sayıya herhangi bir satır basamağı ekleyin.

1. Tamsayıyı ondalık değer mi yoksa hexadecimal değer olarak mı görüntülemek istediğinizi belirleyin.

    - Tamsayıyı `ToString(String)` ondalık değer olarak görüntülemek için, yöntemini çağırın ve *"D* *n"* dizesini, n dizesinin minimum uzunluğunu temsil eden `format` parametrenin değeri olarak geçirin.

    - Tamsayıyı hexadecimal değer olarak görüntülemek için, yöntemini `ToString(String)` çağırın ve *"X* *n"* dizesini, n dizesinin minimum uzunluğunu temsil eden biçim parametresinin değeri olarak geçirin.

Biçim dizesini hem [C#](../../csharp/language-reference/tokens/interpolated.md) hem de [Visual Basic'te](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)enterpolasyonlu bir dizede <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>de kullanabilirsiniz veya bileşik [biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)kullanan bir yöntem <xref:System.String.Format%2A?displayProperty=nameWithType> çağırabilirsiniz.

Aşağıdaki örnek, biçimlendirilmiş sayının toplam uzunluğunun en az sekiz karakter olması için satır aralığı sıfırlarla birkaç tamsayı değerini biçimlendirin.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Belirli sayıda satır aralığı sıfıriçeren bir tamsayıyı deftere almak için

1. Tümsek değerinin kaç tane satır aralığını görüntülemesini istediğinizi belirleyin.

1. Tamsayıyı ondalık değer mi yoksa hexadecimal değer olarak mı görüntülemek istediğinizi belirleyin.

    - Ondalık değer olarak biçimlendirmek için "D" standart biçim belirticisini kullanmanız gerekmektedir.

    - Bir hexadecimal değer olarak biçimlendirme "X" standart biçim belirtici kullanmanız gerektirir.

1. Toplam değerin `ToString("D").Length` veya `ToString("X").Length` yöntemi çağırarak eklenmemiş sayısal dizenin uzunluğunu belirleyin.

1. Biçimlendirilmiş dizeye eklemek istediğiniz satır aralığı sıfırlarının sayısını, eklenmemiş sayısal dize uzunluğuna ekleyin. Satır aralığı sıfırların sayısı nın eklenmesi, dolgulu dizenin toplam uzunluğunu tanımlar.

1. Tamsayı `ToString(String)` değerinin yöntemini çağırın ve ondalık dizeler için "D*n"* ve *n'nin* yastıklı dizenin toplam uzunluğunu temsil ettiği hexadecimal dizeler için "X*n"* dizesini geçirin. "D*n"* veya "X*n*" biçimdize, bileşik biçimlendirmeyi destekleyen bir yöntemde de kullanabilirsiniz.

Aşağıdaki örnek, beş satır sıfıriçeren bir bir bir veyaslama değerini pedleri.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Belirli bir uzunluğa giden sıfırlarla sayısal bir değer emetmek için

1. Ondalık sayı nın solunda kaç basamaklı olmasını istediğinizi belirleyin. Bu toplam basamak sayısına önde gelen sıfırları ekleyin.

1. En az sıfır sayısını temsil etmek için sıfır yer tutucu "0"ı kullanan özel bir sayısal biçim dizesi tanımlayın.

1. Numaranın `ToString(String)` yöntemini çağırın ve özel biçim dizesini geçirin. Ayrıca dize enterpolasyonu veya bileşik biçimlendirme destekleyen bir yöntem ile özel biçim dizek kullanabilirsiniz.

Aşağıdaki örnek, önde gelen sıfırlarla birkaç sayısal değeri biçimlendirür. Sonuç olarak, biçimlendirilmiş sayının toplam uzunluğu ondalık adın solunda en az sekiz basamaktır.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Belirli sayıda satır aralığı sıfıriçeren sayısal bir değere sahip olmak için

1. Sayısal değerin kaç satır önde gelen sıfıra sahip olmasını istediğinizi belirleyin.

1. Ondalık basamak ların solundaki basamak sayısını, eklenmemiş sayısal dizede belirleyin:

    1. Bir sayının dize gösteriminin ondalık nokta simgesi ni içerip içermediğini belirleyin.

    1. Ondalık nokta simgesi içeriyorsa, ondalık noktanın solundaki karakter sayısını belirleyin.

         -veya-

         Ondalık nokta simgesi içermiyorsa, dizenin uzunluğunu belirleyin.

1. Aşağıdakileri kullanan özel bir biçim dizesi oluşturun:

    - Önde gelen sıfırların her biri için dizegörünmesi için sıfır yer tutucu "0"

    - Varsayılan dizedeki her rakamı temsil edecek sıfır yer tutucu veya basamak yer tutucusu "#" olur.

1. Özel biçim dizesini parametre olarak sayının `ToString(String)` yöntemine veya bileşik biçimlendirmeyi destekleyen bir yönteme ver.

Aşağıdaki örnek, beş <xref:System.Double> satır sıfırile iki değer pads.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
