---
title: Dizeleri Tarih/saate Dönüştür
description: Tarih ve saat dizesinden bir tarih saat oluşturmak için tarihleri ve saatleri temsil eden dizeleri ayrıştırma tekniklerini öğrenin.
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.openlocfilehash: 9fba80e4dbe1e4950ed24e7489ac48ea1b6ff20b
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662907"
---
# <a name="parse-date-and-time-strings-in-net"></a>.NET 'teki tarih ve saat dizelerini ayrıştırma

Nesneleri nesnelerine dönüştürmek için ayrıştırma dizeleri <xref:System.DateTime> , tarihlerin ve saatlerin nasıl metin olarak temsil edildiği hakkında bilgi belirtmenizi gerektirir. Farklı kültürler gün, ay ve yıl için farklı siparişler kullanır. Bazı zaman temsilleri 24 saatlik bir saat kullanır, diğerleri "har" ve "PM" i belirler. Bazı uygulamaların yalnızca tarih olması gerekir. Diğerlerinin yalnızca saat olması gerekir. Hala başkalarının hem tarih hem de saati belirtmesi gerekir. Dizeleri nesnelerine dönüştüren Yöntemler, <xref:System.DateTime> istediğiniz biçimler ve uygulamanızın ihtiyaç duyacağı bir tarih ve saate ilişkin ayrıntılı bilgiler sağlamanıza olanak tanır. Metni doğru bir şekilde dönüştürmek için üç alt görev vardır <xref:System.DateTime> :

1. Tarih ve saati temsil eden metnin beklenen biçimini belirtmeniz gerekir.
1. Bir tarih saat biçimi için kültürü belirtebilirsiniz.
1. Metin temsilindeki eksik bileşenlerin tarih ve saat içinde nasıl ayarlanacağını belirtebilirsiniz.

<xref:System.DateTime.Parse%2A>Ve <xref:System.DateTime.TryParse%2A> yöntemleri bir tarih ve saatin birçok yaygın temsilini dönüştürür. <xref:System.DateTime.ParseExact%2A>Ve <xref:System.DateTime.TryParseExact%2A> yöntemleri, bir tarih ve saat biçim dizesi tarafından belirtilen düzene uyan bir dize gösterimini dönüştürür. (Ayrıntılar için [Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md) hakkındaki makalelere bakın.)

Geçerli <xref:System.Globalization.DateTimeFormatInfo> nesne, metnin tarih ve saat olarak nasıl yorumlanacağı üzerinde daha fazla denetim sağlar. Öğesinin özellikleri <xref:System.Globalization.DateTimeFormatInfo> , tarih ve saat ayırıcılarını ve ay, gün ve eras adlarını ve "har" ve "PM" gösterimlerinin biçimini anlatmaktadır. Geçerli iş parçacığı kültürü, <xref:System.Globalization.DateTimeFormatInfo> geçerli kültürü temsil eden bir sağlar. Belirli bir kültür veya özel ayarlar istiyorsanız, <xref:System.IFormatProvider> bir ayrıştırma yönteminin parametresini belirtirsiniz. Parametresi için bir <xref:System.IFormatProvider> <xref:System.Globalization.CultureInfo> kültürü veya bir nesneyi temsil eden bir nesne belirtin <xref:System.Globalization.DateTimeFormatInfo> .

Bir tarih veya saati temsil eden metinde bazı bilgiler eksik olabilir. Örneğin, çoğu kişi "Mart 12" tarihini geçerli yılı temsil eder. Benzer şekilde, "Mart 2018", 2018 yılında Mart ayının ayı temsil eder. Süreyi temsil eden metin yalnızca saat, dakika ve bir har/PM belirtimi içerir.  Ayrıştırma yöntemleri, makul Varsayılanları kullanarak bu eksik bilgileri işler:

- Yalnızca saat varsa, tarih kısmı geçerli tarihi kullanır.
- Yalnızca tarih varsa, saat kısmı gece yarısı olur.
- Yıl bir tarih içinde belirtilmediğinde, geçerli yıl kullanılır.
- Ayın günü belirtilmediğinde ayın ilk adı kullanılır.

Tarih dizede varsa, bu, ayı ve günü veya yıldan birini içermelidir. Zaman varsa, saat ve dakika ya da har/PM göstergesini içermelidir.

<xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault>Bu varsayılan değerleri geçersiz kılmak için sabiti belirtebilirsiniz. Bu sabiti kullandığınızda, eksik yıl, ay veya gün özellikleri değeri değere ayarlanır `1` . [Son kullanılan örnek](#styles-example) <xref:System.DateTime.Parse%2A> Bu davranışı gösterir.

Bir tarih ve saat bileşenine ek olarak, bir tarih ve saatin dize gösterimi, zamanın Eşgüdümlü Evrensel Saat (UTC) ne kadar farklı olduğunu gösteren bir uzaklığa sahip olabilir. Örneğin, "2/14/2007 5:32:00 -7:00" dizesi UTC 'den önceki yedi saat olan bir zamanı tanımlar. Bir zaman içindeki dize gösteriminden bir konum atlanırsa, ayrıştırma <xref:System.DateTime> <xref:System.DateTime.Kind%2A> özelliği olarak ayarlanmış bir nesne döndürür <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> . Bir fark belirtilmişse, ayrıştırma <xref:System.DateTime> <xref:System.DateTime.Kind%2A> özelliği olarak ayarlanmış <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ve değeri makinenizin yerel saat dilimine ayarlanmış olan bir nesne döndürür. Ayrıştırma yöntemiyle bir değer kullanarak bu davranışı değiştirebilirsiniz <xref:System.Globalization.DateTimeStyles> .

Biçim sağlayıcısı, belirsiz bir sayısal tarihi yorumlamak için de kullanılır. "02/03/04" dizesi ile temsil edilen tarihin hangi bileşenlerinin ay, gün ve yıl olduğunu net değildir. Bileşenler, biçim sağlayıcısındaki benzer Tarih biçimlerinin sırasına göre yorumlanır.

## <a name="parse"></a>Ayrıştır

Aşağıdaki örnek, ' a <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> dönüştürmek için yönteminin kullanımını gösterir `string` <xref:System.DateTime> . Bu örnek, geçerli iş parçacığıyla ilişkili kültürü kullanır. <xref:System.Globalization.CultureInfo>Geçerli kültürle ilişkili varsa, giriş dizesi ayrıştırılamaz, bir oluşturulur <xref:System.FormatException> .

> [!TIP]
> Bu makaledeki tüm C# örnekleri tarayıcınızda çalışır. Çıktıyı görmek için **Çalıştır** düğmesine basın. Ayrıca, kendinizi denemek için de düzenleyebilirsiniz.

> [!NOTE]
> Bu örnekler, hem [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/conversions) hem de [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/how-to/conversions)için GitHub docs deposunda mevcuttur.

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Ayrıca, bir dizeyi ayrıştırdığınızda biçimlendirme kuralları kullanılan kültürü açık bir şekilde tanımlayabilirsiniz. <xref:System.Globalization.DateTimeFormatInfo>Özelliği tarafından döndürülen standart nesnelerden birini belirtirsiniz <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> . Aşağıdaki örnek, bir Alman dizesini öğesine ayrıştırmak için bir biçim sağlayıcısı kullanır <xref:System.DateTime> . <xref:System.Globalization.CultureInfo>Kültürü temsil eden bir oluşturur `de-DE` . `CultureInfo`Bu nesne, bu belirli dizeyi başarıyla ayrıştırmayı sağlar. Bu, öğesinin ' de ne olduğunu bu şekilde ayarlar <xref:System.Threading.Thread.CurrentCulture> <xref:System.Threading.Thread.CurrentThread> .

[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Ancak, <xref:System.DateTime.Parse%2A> özel biçim sağlayıcıları belirtmek için yönteminin aşırı yüklerini kullanabilseniz de, yöntemi Standart olmayan biçimlerin ayrıştırılmasını desteklemez. Standart olmayan biçimde ifade edilen bir tarih ve saati ayrıştırmak için, <xref:System.DateTime.ParseExact%2A> bunun yerine yöntemini kullanın.

<a name="styles-example"></a>Aşağıdaki örnek, <xref:System.Globalization.DateTimeStyles> geçerli tarih ve saat bilgilerinin belirtilmemiş alanlara eklenmemesi gerektiğini belirtmek için sabit listesini kullanır <xref:System.DateTime> .

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>Yöntemi, <xref:System.DateTime> belirtilen dize desenlerinden birine uyuyorsa bir dizeyi nesnesine dönüştürür. Belirtilen formlardan biri olmayan bir dize bu yönteme geçirildiğinde, bir <xref:System.FormatException> oluşturulur. Standart Tarih ve saat biçimi belirticilerden birini ya da özel biçim belirticileri birleşimini belirtebilirsiniz. Özel biçim belirticilerini kullanarak, özel bir tanıma dizesi oluşturmanız mümkündür. Belirticilerin açıklaması için [Standart Tarih ve saat biçimi dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)hakkındaki konulara bakın.

Aşağıdaki örnekte, <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi ayrıştırmak için bir dize nesnesi geçti, ardından bir biçim belirticisi ve ardından bir <xref:System.Globalization.CultureInfo> nesne. Bu <xref:System.DateTime.ParseExact%2A> Yöntem yalnızca kültürdeki uzun tarih modelini izleyen dizeleri ayrıştırabilirler `en-US` .

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Ve yöntemlerinin her bir aşırı yüklemesi <xref:System.DateTime.Parse%2A> <xref:System.DateTime.ParseExact%2A> de <xref:System.IFormatProvider> dizenin biçimlendirmesi hakkında kültüre özgü bilgiler sağlayan bir parametreye sahiptir. Bu <xref:System.IFormatProvider> nesne, bir <xref:System.Globalization.CultureInfo> Standart kültürü veya <xref:System.Globalization.DateTimeFormatInfo> özelliği tarafından döndürülen bir nesneyi temsil eden bir nesnedir <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> .  <xref:System.DateTime.ParseExact%2A>Ayrıca, bir veya daha fazla özel tarih ve saat biçimini tanımlayan ek bir dize veya dize dizisi bağımsız değişkeni kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri ayrıştırma](parsing-strings.md)
- [Biçimlendirme türleri](formatting-types.md)
- [.NET içinde tür dönüştürme](type-conversion.md)
- [Standart Tarih ve saat biçimleri](standard-date-and-time-format-strings.md)
- [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
