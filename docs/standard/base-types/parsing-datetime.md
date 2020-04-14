---
title: Dizeleri DateTime'a dönüştürme
description: Tarih ve saat dizesinden bir DateTime oluşturmak için tarihleri ve saatleri temsil eden dizeleri ayrıştırma tekniklerini öğrenin.
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
ms.openlocfilehash: 4b3f0bdb3ade784f929718a3350ed3dec0c572f1
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242653"
---
# <a name="parse-date-and-time-strings-in-net"></a>.NET'teki tarih ve zaman dizelerini ayrışt

Dizeleri nesnelere dönüştürmek için <xref:System.DateTime> ayrıştMa, tarih ve saatlerin metin olarak nasıl temsil edildiği hakkında bilgi belirtmenizi gerektirir. Farklı kültürler gün, ay ve yıl için farklı siparişler kullanır. Bazı zaman gösterimleri 24 saatlik bir saat kullanırken, diğerleri ve PM belirtir. Bazı uygulamaların yalnızca tarih eihtiyacı vardır. Diğerlerinin sadece zamana ihtiyacı var. Yine de diğerlerinin hem tarih hem de saat belirtmeleri gerekir. Dizeleri nesnelere <xref:System.DateTime> dönüştüren yöntemler, beklediğiniz biçimler ve uygulamanızın ihtiyaç duyduğu tarih ve saatöğeleri hakkında ayrıntılı bilgi sağlamanıza olanak tanır. Metni <xref:System.DateTime>doğru bir şekilde bir

1. Tarih ve saati temsil eden metnin beklenen biçimini belirtmeniz gerekir.
1. Bir tarih saatinin biçimi için kültürü belirtebilirsiniz.
1. Metin gösterimindeki eksik bileşenlerin tarih ve saat içinde nasıl ayarlandığı belirtebilirsiniz.

Ve <xref:System.DateTime.Parse%2A> <xref:System.DateTime.TryParse%2A> yöntemler, bir tarih ve saatin birçok yaygın temsilini dönüştürür. Ve <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> yöntemler, tarih ve saat biçimi dizetarafından belirtilen desene uyan bir dize gösterimini dönüştürür. (Ayrıntılar için [standart tarih ve saat biçimi dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçimi dizeleri](custom-date-and-time-format-strings.md) ile ilgili makalelere bakın.)

Geçerli <xref:System.Globalization.DateTimeFormatInfo> nesne, metnin tarih ve saat olarak nasıl yorumlanması gerektiği üzerinde daha fazla denetim sağlar. Tarih <xref:System.Globalization.DateTimeFormatInfo> ve saat ayırıcılarının özelliklerini, ay, gün ve dönem adlarını ve ve PM tanımlamalarının biçimini açıklar. Geçerli iş parçacığı <xref:System.Globalization.DateTimeFormatInfo> kültürü, geçerli kültürü temsil eden bir sözcük sağlar. Belirli bir kültür veya özel ayarlar istiyorsanız, ayrıştma yönteminin parametresini <xref:System.IFormatProvider> belirtirsiniz. Parametre <xref:System.IFormatProvider> için, bir <xref:System.Globalization.CultureInfo> kültürü veya nesneyi temsil <xref:System.Globalization.DateTimeFormatInfo> eden bir nesne belirtin.

Bir tarih veya saati temsil eden metin bazı bilgiler eksik olabilir. Örneğin, çoğu kişi "12 Mart" tarihinin geçerli yılı temsil edeceğini varsayar. Benzer şekilde, "Mart 2018" 2018 yılının Mart ayını temsil eder. Zamanı temsil eden metin genellikle yalnızca saat, dakika ve AM/PM ataması içerir.  Ayrışdırma yöntemleri makul varsayılanları kullanarak bu eksik bilgileri işler:

- Yalnızca saat mevcut olduğunda, tarih bölümü geçerli tarihi kullanır.
- Yalnızca tarih bulunduğunda, zaman kısmı gece yarısıdır.
- Yıl bir tarihte belirtilmediğinde, geçerli yıl kullanılır.
- Ayın günü belirtilmediğinde, ayın ilk günü kullanılır.

Tarih dizede varsa, ayı ve gün veya yıldan birini içermelidir. Saat varsa, saati ve dakikaları veya AM/PM atasını içermelidir.

Bu varsayılanları <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> geçersiz kılmak için sabiti belirtebilirsiniz. Bu sabiti kullandığınızda, eksik yıl, ay veya gün `1`özellikleri değere ayarlanır. Son [örnek](#styles-example) <xref:System.DateTime.Parse%2A> bu davranışı gösterir.

Bir tarih ve saat bileşenine ek olarak, bir tarih ve saatin dize gösterimi, sürenin Eşgüdümlü Evrensel Zaman'dan (UTC) ne kadar farklı olduğunu gösteren bir ofset içerebilir. Örneğin, "14.02.2007 5:32:00 -7:00" dizesi UTC'den yedi saat önce olan bir zamanı tanımlar. Bir ofset, bir zamanın dize gösteriminden atlanırsa, <xref:System.DateTime> ayrıştırma <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>özelliği 'ne ayarlanmış bir nesneyi <xref:System.DateTime.Kind%2A> döndürür. Bir ofset belirtilirse, ayrıştırma <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ayarlanmış ve değeri makinenizin yerel saat dilimine ayarlanmış bir <xref:System.DateTime> nesneyi döndürür. Ayrıştma yöntemiyle <xref:System.Globalization.DateTimeStyles> bir değer kullanarak bu davranışı değiştirebilirsiniz.
  
Biçim sağlayıcısı, belirsiz bir sayısal tarihi yorumlamak için de kullanılır. "02/03/04" dizesinin temsil ettiği tarihin hangi bileşenlerinin ay, gün ve yıl olduğu açık değildir. Bileşenler, biçim sağlayıcısındaki benzer tarih biçimlerinin sırasına göre yorumlanır.

## <a name="parse"></a>Ayrıştır

Aşağıdaki örnekte, <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> a'yı `string` bir . <xref:System.DateTime> Bu örnek, geçerli iş parçacığı ile ilişkili kültür kullanır. Geçerli <xref:System.Globalization.CultureInfo> kültürle ilişkili giriş dizesini ayrıştıramıyorsa, a <xref:System.FormatException> atılır.

> [!TIP]
> Bu makaledeki tüm C# örnekleri tarayıcınızda çalışır. Çıktıyı görmek için **Çalıştır** düğmesine basın. Ayrıca, bunları kendinizi denemek için de edinebilirsiniz.

> [!NOTE]
> Bu örnekler Hem [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/conversions) hem de [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/how-to/conversions)için GitHub dokümanları repo'sunda mevcuttur. Veya, [C#](https://github.com/dotnet/docs/blob/master/samples/snippets/csharp/how-to/conversions.zip) veya [Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/how-to/conversions.zip)için bir zip dosyası olarak proje indirebilirsiniz.

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Ayrıca, bir dizeyi ayrıştırken biçimlendirme kuralları kullanılan kültürü de açıkça tanımlayabilirsiniz. Özellik tarafından döndürülen <xref:System.Globalization.DateTimeFormatInfo> standart nesnelerden <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> birini belirtirsiniz. Aşağıdaki örnekte, bir Alman dizesini ayrıştmak <xref:System.DateTime>için bir biçim sağlayıcısı kullanır. Kültürü temsil <xref:System.Globalization.CultureInfo> eden bir şey yaratır. `de-DE` Bu `CultureInfo` nesne, bu özel dize başarılı ayrışma sağlar. Bu, ne olursa olsun ayarı <xref:System.Threading.Thread.CurrentCulture> <xref:System.Threading.Thread.CurrentThread>engellenir .  
  
[!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Ancak, özel biçim sağlayıcılarını <xref:System.DateTime.Parse%2A> belirtmek için yöntemin aşırı yüklerini kullanabilmenize rağmen, yöntem standart dışı biçimleri ayrıştmayı desteklemez. Standart olmayan bir biçimde ifade edilen bir tarih ve <xref:System.DateTime.ParseExact%2A> saati ayrıştmak için yöntemi kullanın.  

<a name="styles-example"></a>Aşağıdaki örnek, <xref:System.Globalization.DateTimeStyles> geçerli tarih ve saat bilgilerinin belirtilmeyen <xref:System.DateTime> alanlara eklenmemesi gerektiğini belirtmek için numaralandırmayı kullanır.  

[!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>Parseexact

Yöntem, <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> belirtilen dize <xref:System.DateTime> desenlerinden birine uyuyorsa, bir dizeyi nesneye dönüştürür. Belirtilen formlardan biri olmayan bir dize bu yönteme <xref:System.FormatException> geçirildiğinde, bir atılır. Standart tarih ve saat biçimi belirticilerinden birini veya özel biçim belirticilerinin bir birleşimini belirtebilirsiniz. Özel biçim belirteçlerini kullanarak, özel bir tanıma dizesi oluşturmanız mümkündür. Belirteçlerin bir açıklama için, standart [tarih ve saat biçimi dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçimi dizeleri](custom-date-and-time-format-strings.md)konulara bakın.  

Aşağıdaki örnekte, <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntem ayrıştırmak için bir dize nesnesi geçirilir, <xref:System.Globalization.CultureInfo> ardından bir biçim belirtimi, ardından bir nesne. Bu <xref:System.DateTime.ParseExact%2A> yöntem yalnızca `en-US` kültürdeki uzun tarih deseni izleyen dizeleri ayrıştabilir.  

[!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Her aşırı yükleme <xref:System.DateTime.Parse%2A> <xref:System.DateTime.ParseExact%2A> ve yöntemler <xref:System.IFormatProvider> de dize biçimlendirme hakkında kültüre özgü bilgi sağlayan bir parametre vardır. Bu <xref:System.IFormatProvider> nesne, <xref:System.Globalization.CultureInfo> standart bir kültürü veya <xref:System.Globalization.DateTimeFormatInfo> <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özellik tarafından döndürülen bir nesneyi temsil eden bir nesnedir.  <xref:System.DateTime.ParseExact%2A>ayrıca, bir veya daha fazla özel tarih ve saat biçimini tanımlayan ek bir dize veya dize dizi bağımsız değişkeni kullanır.  

## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Ayrıştırma](parsing-strings.md)
- [Biçimlendirme Türleri](formatting-types.md)
- [.NET'te Tür Dönüştürme](type-conversion.md)
- [Standart tarih ve saat biçimleri](standard-date-and-time-format-strings.md)
- [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
