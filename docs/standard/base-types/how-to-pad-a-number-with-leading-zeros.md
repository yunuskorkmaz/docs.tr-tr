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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131982"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma

"D" [Standart sayısal biçim dizesini](../../../docs/standard/base-types/standard-numeric-format-strings.md) bir duyarlık belirticisiyle kullanarak bir tamsayıya önde gelen sıfırlar ekleyebilirsiniz. [Özel bir sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md)kullanarak, hem tamsayı hem de kayan nokta numaralarına önde sıfır ekleyebilirsiniz. Bu makalede, her iki yöntemin de bir sayıyı baştaki sıfırlarla doldurma yöntemi gösterilmektedir.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Bir tamsayıyı önünde sıfır ile belirli bir uzunluğa göre doldurma

1. Tamsayı değerinin görüntülenmesini istediğiniz en az basamak sayısını belirleme. Bu numaraya öndeki rakamları ekleyin.

1. Tamsayıyı ondalık değer veya onaltılık bir değer olarak göstermek isteyip istemediğinizi belirleme.

    - Tamsayıyı ondalık değer olarak göstermek için `ToString(String)` yöntemini çağırın ve "D*n*" dizesini `format` parametresinin değeri olarak geçirin; burada *n* , dizenin minimum uzunluğunu temsil eder.

    - Tamsayıyı onaltılık bir değer olarak göstermek için, `ToString(String)` yöntemini çağırın ve "X*n*" dizesini biçim parametresinin değeri olarak geçirin; burada *n* , dizenin minimum uzunluğunu temsil eder.

Ayrıca, biçim dizesini hem [C#](../../csharp/language-reference/tokens/interpolated.md) hem de [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)içindeki bir enterpolasyonlu dize içinde de kullanabilir veya [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)kullanan <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>gibi bir yöntemi çağırabilirsiniz.

Aşağıdaki örnek, biçimlendirilen sayının toplam uzunluğu en az sekiz karakter olacak şekilde, bazı tamsayı değerlerini öndeki sıfırlar ile biçimlendirir.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Bir tamsayıyı belirli bir baştaki sıfır sayısıyla doldurma

1. Tamsayı değerinin kaç tane önde görüntülenmesini istediğinizi saptayın.

1. Tamsayıyı ondalık değer veya onaltılık bir değer olarak göstermek isteyip istemediğinizi belirleme.

    - Bunu bir ondalık değer olarak biçimlendirmek için "D" standart biçim belirticisini kullanmanız gerekir.

    - Onaltılık değer olarak biçimlendirmek için "X" Standart Biçim belirleyicisi kullanmanız gerekir.

1. Tamsayı değerinin `ToString("D").Length` veya `ToString("X").Length` metodunu çağırarak, unununnumernumeric dizenin uzunluğunu saptayın.

1. Sayısal olmayan dizenin uzunluğuna göre biçimlendirilen dizeye eklemek istediğiniz öndeki sıfırlar sayısını ekleyin. Baştaki sıfırların sayısını eklemek, doldurulmuş dizenin toplam uzunluğunu tanımlar.

1. Tamsayı değerinin `ToString(String)` yöntemini çağırın ve onaltılık dizeler için "D*n*" dizesini ve onaltılık dizeler Için "X*n*" dizesini geçirin; burada *n* , doldurulmuş dizenin toplam uzunluğunu temsil eder. Bileşik biçimlendirmeyi destekleyen bir yöntemde "D*n*" veya "X*n*" biçim dizesini de kullanabilirsiniz.

Aşağıdaki örnek, beş önde sıfır ile bir tamsayı değeri alt Pad.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Sayısal bir değeri öndeki sıfırlar ile belirli bir uzunluğa göre doldurma

1. Sayının dize gösteriminin kaç basamak olmasını istediğinizi belirleme. Bu toplam basamak sayısında öndeki sıfırları ekleyin.

1. En az sıfır sayısını temsil etmek için sıfır "0" yer tutucusunu kullanan özel bir sayısal biçim dizesi tanımlayın.

1. Sayının `ToString(String)` yöntemini çağırın ve özel biçim dizesine geçirin. Dize ilişkilendirme ile veya bileşik biçimlendirmeyi destekleyen bir yöntemle özel biçim dizesini de kullanabilirsiniz.

Aşağıdaki örnek, öndeki sıfırlar ile birkaç sayısal değeri biçimlendirir. Sonuç olarak, biçimlendirilen sayının toplam uzunluğu, ondalık ayırıcının solunda en az sekiz haneye sahiptir.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Sayısal bir değeri belirli bir satır başına sıfır sayısıyla doldurma

1. Sayısal değerin kaç tane önde olacağını istediğinizi belirleme.

1. Undoldurulmuş sayısal dizedeki Decimal öğesinin solundaki basamak sayısını belirleme:

    1. Bir sayının dize temsilinin bir Decimal Point simgesi içerip içermediğini belirleme.

    1. Bir ondalık nokta sembolü içeriyorsa, ondalık noktanın solundaki karakter sayısını saptayın.

         veya

         Bir ondalık nokta simgesi içermiyorsa, dizenin uzunluğunu saptayın.

1. Şunu kullanan bir özel biçim dizesi oluşturun:

    - Baştaki sıfırların her biri için dizede görünecek sıfır yer tutucusu "0".

    - Varsayılan dizedeki her basamağı temsil eden sıfır yer tutucusu veya "#" basamak yer tutucusu.

1. Özel biçim dizesini, sayının `ToString(String)` yöntemine ya da bileşik biçimlendirmeyi destekleyen bir yönteme parametre olarak sağlayın.

Aşağıdaki örnek, beş önde gelen sıfır ile iki <xref:System.Double> değerini defterler.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
