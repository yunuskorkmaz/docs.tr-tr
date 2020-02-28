---
title: "Nasıl yapılır: dizeleri DateTime 'a dönüştürme"
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
ms.openlocfilehash: 9555304e570226b2ed3b040735cf099b5a018f93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156549"
---
# <a name="parsing-date-and-time-strings-in-net"></a>.NET 'teki tarih ve saat dizelerini ayrıştırma

Nesneleri <xref:System.DateTime> dönüştürmek için ayrıştırma dizeleri, tarihlerin ve saatlerin nasıl metin olarak temsil edildiği hakkında bilgi belirtmenizi gerektirir. Farklı kültürler gün, ay ve yıl için farklı siparişler kullanır. Bazı zaman temsilleri 24 saatlik bir saat kullanır, diğerleri "har" ve "PM" i belirler. Bazı uygulamaların yalnızca tarih olması gerekir. Diğerlerinin yalnızca saat olması gerekir. Hala başkalarının hem tarih hem de saati belirtmesi gerekir. Dizeleri <xref:System.DateTime> nesnelerine dönüştüren Yöntemler, istediğiniz biçimler ve uygulamanızın ihtiyaç duyacağı bir tarih ve saatin öğeleri hakkında ayrıntılı bilgi sağlamanıza olanak tanır. Metni doğru bir <xref:System.DateTime>dönüştürmek için üç alt görev vardır:

1. Tarih ve saati temsil eden metnin beklenen biçimini belirtmeniz gerekir.
1. Bir tarih saat biçimi için kültürü belirtebilirsiniz.
1. Metin temsilindeki eksik bileşenlerin tarih ve saat içinde nasıl ayarlanacağını belirtebilirsiniz.

<xref:System.DateTime.Parse%2A> ve <xref:System.DateTime.TryParse%2A> yöntemleri bir tarih ve saatin birçok yaygın temsilini dönüştürür. <xref:System.DateTime.ParseExact%2A> ve <xref:System.DateTime.TryParseExact%2A> yöntemleri, bir tarih ve saat biçim dizesi tarafından belirtilen düzene uyan bir dize gösterimini dönüştürür. (Ayrıntılar için [Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md) hakkındaki makalelere bakın.)

Geçerli <xref:System.Globalization.DateTimeFormatInfo> nesnesi, metnin tarih ve saat olarak nasıl yorumlanacağı üzerinde daha fazla denetim sağlar. <xref:System.Globalization.DateTimeFormatInfo> özellikleri, tarih ve saat ayırıcıları ve ay, gün ve eras adlarını ve "har" ve "PM" gösterimlerinin biçimini anlatmaktadır. Geçerli iş parçacığı kültürü geçerli kültürü temsil eden bir <xref:System.Globalization.DateTimeFormatInfo> sağlar. Belirli bir kültür veya özel ayarlar istiyorsanız, ayrıştırma yönteminin <xref:System.IFormatProvider> parametresini belirtirsiniz. <xref:System.IFormatProvider> parametresi için bir kültürü veya <xref:System.Globalization.DateTimeFormatInfo> nesnesini temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi belirtin.

Bir tarih veya saati temsil eden metinde bazı bilgiler eksik olabilir. Örneğin, çoğu kişi "Mart 12" tarihini geçerli yılı temsil eder. Benzer şekilde, "Mart 2018", 2018 yılında Mart ayının ayı temsil eder. Süreyi temsil eden metin yalnızca saat, dakika ve bir har/PM belirtimi içerir.  Ayrıştırma yöntemleri, makul Varsayılanları kullanarak bu eksik bilgileri işler:

- Yalnızca saat varsa, tarih kısmı geçerli tarihi kullanır.
- Yalnızca tarih varsa, saat kısmı gece yarısı olur.
- Yıl bir tarih içinde belirtilmediğinde, geçerli yıl kullanılır.
- Ayın günü belirtilmediğinde ayın ilk adı kullanılır.

Tarih dizede varsa, bu, ayı ve günü veya yıldan birini içermelidir. Zaman varsa, saat ve dakika ya da har/PM göstergesini içermelidir.

Bu varsayılan değerleri geçersiz kılmak için <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> sabiti belirtebilirsiniz. Bu sabiti kullandığınızda, eksik yıl, ay veya gün özellikleri `1`değere ayarlanır. <xref:System.DateTime.Parse%2A> kullanan [son örnek](#styles-example) bu davranışı gösterir.

Bir tarih ve saat bileşenine ek olarak, bir tarih ve saatin dize gösterimi, zamanın Eşgüdümlü Evrensel Saat (UTC) ne kadar farklı olduğunu gösteren bir uzaklığa sahip olabilir. Örneğin, "2/14/2007 5:32:00 -7:00" dizesi UTC 'den önceki yedi saat olan bir zamanı tanımlar. Bir zaman içindeki dize gösteriminden bir konum atlanırsa, ayrıştırma, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>olarak ayarlanmış bir <xref:System.DateTime> nesnesi döndürür. Bir fark belirtilmişse, ayrıştırma, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local?displayProperty=nameWithType> olarak ayarlanmış ve değeri makinenizin yerel saat dilimine ayarlanmış olarak <xref:System.DateTime> bir nesne döndürür. Ayrıştırma yöntemiyle bir <xref:System.Globalization.DateTimeStyles> değeri kullanarak bu davranışı değiştirebilirsiniz.
  
Biçim sağlayıcısı, belirsiz bir sayısal tarihi yorumlamak için de kullanılır. "02/03/04" dizesi ile temsil edilen tarihin hangi bileşenlerinin ay, gün ve yıl olduğunu net değildir. Bileşenler, biçim sağlayıcısındaki benzer Tarih biçimlerinin sırasına göre yorumlanır.

## <a name="parse"></a>MAZ

Aşağıdaki örnek, bir `string` <xref:System.DateTime>dönüştürmek için <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> yönteminin kullanımını gösterir. Bu örnek, geçerli iş parçacığıyla ilişkili kültürü kullanır. Geçerli kültür ile ilişkili <xref:System.Globalization.CultureInfo> giriş dizesini ayrıştıramaz, bir <xref:System.FormatException> oluşturulur.

> [!TIP]
> Bu makaledeki C# tüm örnekler tarayıcınızda çalışır. Çıktıyı görmek için **Çalıştır** düğmesine basın. Ayrıca, kendinizi denemek için de düzenleyebilirsiniz.

> [!NOTE]
> Bu örnekler, hem hem de [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions)için GitHub docs deposunda mevcuttur. Ya da, projeyi veya [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) [Visual Basic](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip)için bir zip dosyası olarak indirebilirsiniz.

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Ayrıca, bir dizeyi ayrıştırdığınızda biçimlendirme kuralları kullanılan kültürü açık bir şekilde tanımlayabilirsiniz. <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği tarafından döndürülen standart <xref:System.Globalization.DateTimeFormatInfo> nesnelerinden birini belirtirsiniz. Aşağıdaki örnek bir <xref:System.DateTime>bir Alman dizeyi ayrıştırmak için bir biçim sağlayıcısı kullanır. `de-DE` kültürünü temsil eden bir <xref:System.Globalization.CultureInfo> oluşturur. Bu `CultureInfo` nesnesi bu dizenin başarıyla ayrıştırılmasını sağlar. Bu, <xref:System.Threading.Thread.CurrentThread><xref:System.Threading.Thread.CurrentCulture> hangi ayarın olduğunu önceden açar.  
  
[!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Ancak, özel biçim sağlayıcıları belirtmek için <xref:System.DateTime.Parse%2A> yönteminin aşırı yüklerini kullanabilseniz de, yöntem standart olmayan biçimlerin ayrıştırılmasını desteklemez. Standart olmayan biçimde ifade edilen bir tarih ve saati ayrıştırmak için, bunun yerine <xref:System.DateTime.ParseExact%2A> yöntemini kullanın.  

<a name="styles-example"></a>Aşağıdaki örnek, belirtilmeyen alanlar için geçerli tarih ve saat bilgilerinin <xref:System.DateTime> eklenmemesi gerektiğini belirtmek için <xref:System.Globalization.DateTimeStyles> numaralandırmayı kullanır.  

[!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi, belirtilen dize desenlerinden birine uyuyorsa bir dizeyi <xref:System.DateTime> nesnesine dönüştürür. Belirtilen formlardan biri olmayan bir dize bu yönteme geçirildiğinde, bir <xref:System.FormatException> oluşturulur. Standart Tarih ve saat biçimi belirticilerden birini ya da özel biçim belirticileri birleşimini belirtebilirsiniz. Özel biçim belirticilerini kullanarak, özel bir tanıma dizesi oluşturmanız mümkündür. Belirticilerin açıklaması için [Standart Tarih ve saat biçimi dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)hakkındaki konulara bakın.  

Aşağıdaki örnekte <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi ayrıştırmak için bir dize nesnesi geçti, ardından bir biçim belirticisi ve ardından bir <xref:System.Globalization.CultureInfo> nesnesi. Bu <xref:System.DateTime.ParseExact%2A> yöntemi yalnızca `en-US` kültürünün uzun tarih modelini izleyen dizeleri ayrıştırabilirler.  

[!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

<xref:System.DateTime.Parse%2A> ve <xref:System.DateTime.ParseExact%2A> yöntemlerinin her bir aşırı yüklemesinin, dizenin biçimlendirmesi hakkında kültüre özgü bilgiler sağlayan bir <xref:System.IFormatProvider> parametresi de vardır. Bu <xref:System.IFormatProvider> nesnesi, <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği tarafından döndürülen standart bir kültürü veya <xref:System.Globalization.DateTimeFormatInfo> nesnesini temsil eden bir <xref:System.Globalization.CultureInfo> nesnesidir.  <xref:System.DateTime.ParseExact%2A> Ayrıca bir veya daha fazla özel tarih ve saat biçimi tanımlayan ek bir dize veya dize dizisi bağımsız değişkeni kullanır.  

## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Ayrıştırma](parsing-strings.md)
- [Biçimlendirme Türleri](formatting-types.md)
- [.NET içinde Tür Dönüştürme](type-conversion.md)
- [Standart Tarih ve saat biçimleri](standard-date-and-time-format-strings.md)
- [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
