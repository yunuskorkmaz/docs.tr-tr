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
ms.openlocfilehash: ef18fb1bb7b1592a4e92866028868bf1cf793bbf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290467"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma

"D" [Standart sayısal biçim dizesini](standard-numeric-format-strings.md) bir duyarlık belirticisiyle kullanarak bir tamsayıya önde gelen sıfırlar ekleyebilirsiniz. [Özel bir sayısal biçim dizesi](custom-numeric-format-strings.md)kullanarak, hem tamsayı hem de kayan nokta numaralarına önde sıfır ekleyebilirsiniz. Bu makalede, her iki yöntemin de bir sayıyı baştaki sıfırlarla doldurma yöntemi gösterilmektedir.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Bir tamsayıyı önünde sıfır ile belirli bir uzunluğa göre doldurma

1. Tamsayı değerinin görüntülenmesini istediğiniz en az basamak sayısını belirleme. Bu numaraya öndeki rakamları ekleyin.

1. Tamsayıyı ondalık değer veya onaltılık bir değer olarak göstermek isteyip istemediğinizi belirleme.

    - Tamsayıyı bir ondalık değer olarak göstermek için `ToString(String)` metodunu çağırın ve "D*n*" dizesini parametresinin değeri olarak geçirin `format` ; burada *n* , dizenin minimum uzunluğunu temsil eder.

    - Tamsayıyı onaltılık bir değer olarak göstermek için `ToString(String)` metodunu çağırın ve "X*n*" dizesini biçim parametresinin değeri olarak geçirin; burada *n* , dizenin minimum uzunluğunu temsil eder.

Ayrıca, biçim dizesini hem [C#](../../csharp/language-reference/tokens/interpolated.md) hem de [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)enterpolasyonlu bir dizedeki de kullanabilirsiniz ya da <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> [Bileşik biçimlendirme](composite-formatting.md)kullanan veya gibi bir yöntemi çağırabilirsiniz.

Aşağıdaki örnek, biçimlendirilen sayının toplam uzunluğu en az sekiz karakter olacak şekilde, bazı tamsayı değerlerini öndeki sıfırlar ile biçimlendirir.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Bir tamsayıyı belirli bir baştaki sıfır sayısıyla doldurma

1. Tamsayı değerinin kaç tane önde görüntülenmesini istediğinizi saptayın.

1. Tamsayıyı ondalık değer veya onaltılık bir değer olarak göstermek isteyip istemediğinizi belirleme.

    - Bunu bir ondalık değer olarak biçimlendirmek için "D" standart biçim belirticisini kullanmanız gerekir.

    - Onaltılık değer olarak biçimlendirmek için "X" Standart Biçim belirleyicisi kullanmanız gerekir.

1. Tamsayı değerinin veya metodunu çağırarak, unununnumeric dizenin uzunluğunu belirleme `ToString("D").Length` `ToString("X").Length` .

1. Sayısal olmayan dizenin uzunluğuna göre biçimlendirilen dizeye eklemek istediğiniz öndeki sıfırlar sayısını ekleyin. Baştaki sıfırların sayısını eklemek, doldurulmuş dizenin toplam uzunluğunu tanımlar.

1. Tamsayı değerinin `ToString(String)` metodunu çağırın ve "D*n*" dizesini ondalık dizeler Için ve "X*n*" dizesini, onaltılık dizeler için geçirin; burada *n* , doldurulmuş dizenin toplam uzunluğunu temsil eder. Bileşik biçimlendirmeyi destekleyen bir yöntemde "D*n*" veya "X*n*" biçim dizesini de kullanabilirsiniz.

Aşağıdaki örnek, beş önde sıfır ile bir tamsayı değeri alt Pad.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Sayısal bir değeri öndeki sıfırlar ile belirli bir uzunluğa göre doldurma

1. Sayının dize gösteriminin kaç basamak olmasını istediğinizi belirleme. Bu toplam basamak sayısında öndeki sıfırları ekleyin.

1. En az sıfır sayısını temsil etmek için sıfır "0" yer tutucusunu kullanan özel bir sayısal biçim dizesi tanımlayın.

1. Sayının `ToString(String)` metodunu çağırın ve özel biçim dizesine geçirin. Dize ilişkilendirme ile veya bileşik biçimlendirmeyi destekleyen bir yöntemle özel biçim dizesini de kullanabilirsiniz.

Aşağıdaki örnek, öndeki sıfırlar ile birkaç sayısal değeri biçimlendirir. Sonuç olarak, biçimlendirilen sayının toplam uzunluğu, ondalık ayırıcının solunda en az sekiz haneye sahiptir.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Sayısal bir değeri belirli bir satır başına sıfır sayısıyla doldurma

1. Sayısal değerin kaç tane önde olacağını istediğinizi belirleme.

1. Undoldurulmuş sayısal dizedeki Decimal öğesinin solundaki basamak sayısını belirleme:

    1. Bir sayının dize temsilinin bir Decimal Point simgesi içerip içermediğini belirleme.

    1. Bir ondalık nokta sembolü içeriyorsa, ondalık noktanın solundaki karakter sayısını saptayın.

         -veya-

         Bir ondalık nokta simgesi içermiyorsa, dizenin uzunluğunu saptayın.

1. Şunu kullanan bir özel biçim dizesi oluşturun:

    - Baştaki sıfırların her biri için dizede görünecek sıfır yer tutucusu "0".

    - Varsayılan dizedeki her basamağı temsil eden sıfır yer tutucusu veya "#" basamak yer tutucusu.

1. Özel biçim dizesini, sayının `ToString(String)` yöntemine ya da bileşik biçimlendirmeyi destekleyen bir yönteme parametre olarak sağlayın.

Aşağıdaki örnek, <xref:System.Double> beş öndeki sıfırlar ile iki değeri alt Pad.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel sayısal biçim dizeleri](custom-numeric-format-strings.md)
- [Standart sayısal biçim dizeleri](standard-numeric-format-strings.md)
- [Bileşik biçimlendirme](composite-formatting.md)
