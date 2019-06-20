---
title: 'Nasıl yapılır: dizeleri DateTime olarak dönüştürme'
description: Tarihler ve saatler tarih ve saat dizesi bir tarih/saat oluşturulacağını temsil eden dizeleri ayrıştırılacak teknikleri öğrenin.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4217221cc5199b9d8904be1ca3073878378b4e9
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268174"
---
# <a name="parsing-date-and-time-strings-in-net"></a>Tarih ve saat dizelerini .NET ayrıştırma

Bunları dönüştürmek için dizeleri ayrıştırma <xref:System.DateTime> nesneleri tarihleri ve saatleri metin olarak nasıl temsil hakkında bilgi belirtmenizi gerektirir. Farklı kültürler farklı siparişleri gün, ay ve yıl için kullanın. 24 saatlik zaman bazı gösterimler kullanın, diğerleri "AM" ve "PM" belirtin Bazı uygulamalar, yalnızca tarih gerekir. Diğerleri yalnızca süre gerekir. Yine de diğer tarih ve saat belirtmeniz gerekir. Dizeleri için dönüştürme yöntemleri <xref:System.DateTime> nesneleri, uygulama ihtiyaçlarınızı beklediğiniz biçimleri ve bir tarihin öğeleri hakkında ayrıntılı bilgi sağlar ve sağlar. Doğru metne dönüştürme için üç alt görevler vardır. bir <xref:System.DateTime>:

1. Bir tarih ve saatini temsil eden metin biçimiyle belirtmeniz gerekir.
1. Kültür için tarih saat biçiminde belirtebilirsiniz.
1. Nasıl eksik bileşenleri belirtebilir metin gösterimi tarih ve saat ayarlanır.

<xref:System.DateTime.Parse%2A> Ve <xref:System.DateTime.TryParse%2A> yöntemleri bir tarih ve saat birçok ortak temsillerini Dönüştür. <xref:System.DateTime.ParseExact%2A> Ve <xref:System.DateTime.TryParseExact%2A> yöntemleri bir tarih ve saat biçim dizesi tarafından belirtilen düzene uyan bir dize gösterimi Dönüştür. (Makaleleri görmek [standart tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md) Ayrıntılar için.)

Geçerli <xref:System.Globalization.DateTimeFormatInfo> nesnesi, bir tarih ve saat metin nasıl yorumlanmalıdır üzerinde daha fazla denetim sağlar. Özellikleri bir <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat ayırıcısı ve ay, gün ve dönemleri ve biçimi adları için "AM" ve "PM" ifadelerini açıklar. Geçerli iş parçacığı kültürünü sağlayan bir <xref:System.Globalization.DateTimeFormatInfo> geçerli kültürü temsil eden. Belirttiğiniz belirli bir kültür veya özel ayarlar isterseniz, <xref:System.IFormatProvider> ayrıştırma yönteminin parametresi. İçin <xref:System.IFormatProvider> parametresi belirtin bir <xref:System.Globalization.CultureInfo> bir kültürü temsil eden bir nesne veya <xref:System.Globalization.DateTimeFormatInfo> nesne.

Bir tarih veya saat temsil eden metin bazı bilgiler eksik olabilir. Örneğin, çoğu kişi "12 Mart'tan" geçerli yıl temsil eden tarih varsayın. Benzer şekilde, "Mart 2018" Mart 2018 yılı, ayı temsil eder. Metin temsil eden saat genellikle yalnızca yok, saat, dakika ve AM/PM gösterimi içerir.  Ayrıştırma yöntemlerinin makul varsayılanlar kullanarak bu eksik bilgiyi işler:

- Yalnızca mevcut olduğunda, tarih bölümü geçerli tarihi kullanır.
- Yalnızca tarih mevcut olduğunda, saat bölümü gece yarısıdır.
- Geçerli yıl, yılın bir tarih belirtilmemiş olduğunda kullanılır.
- Ayın ilk günü, ayın gününü belirtilmemiş olduğunda kullanılır.

Tarih dizesinde ise, ay ve gün veya yıl birini içermelidir. Zaman varsa, saat ve dakika veya AM/PM göstergesi içermelidir.

Belirtebileceğiniz <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> bu Varsayılanları geçersiz kılmak üzere sabiti. Bu sabit, eksik bir yıl, ay kullandığınız ya da günlük özellikleri değerine ayarlanır `1`. [Son örnek](#styles-example) kullanarak <xref:System.DateTime.Parse%2A> Bu davranış gösterir.

Bir tarih ve saat bileşeni ek olarak, bir tarih ve saat dize gösterimini Eşgüdümlü Evrensel Saat (UTC) ne kadar süre farklılık gösteren bir uzaklık içerebilir. Örneğin, dize "14/2/2007 5:32:00 -7:00" yani yedi saatler UTC'den önceki bir süreyi tanımlar. Döndürür bir saatin dize temsilinden bir uzaklık atlanırsa, ayrıştırma bir <xref:System.DateTime> nesnesi ile kendi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Döndürür bir uzaklık belirtilirse, ayrıştırma bir <xref:System.DateTime> nesnesi ile kendi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ve değerini makinenizde yerel saat dilimine ayarlanır. Kullanarak bu davranışı değiştirebilirsiniz bir <xref:System.Globalization.DateTimeStyles> ayrıştırma yönteminin değeri.
  
Biçim sağlayıcısı, belirsiz bir sayısal tarih yorumlamak için de kullanılır. Bu ay, gün ve yıl "02/03/04" dizesi tarafından temsil edilen tarih bileşenlerini olduğu açık değildir. Bileşenleri biçimi sağlayıcısındaki benzer tarih biçimleri sırasına göre yorumlanır.

## <a name="parse"></a>Ayrıştırma

Aşağıdaki örnek, kullanımını gösterir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> dönüştürmek için yöntemi bir `string` içine bir <xref:System.DateTime>. Bu örnek, geçerli iş parçacığıyla ilişkilendirilmiş kültürü kullanır. Varsa <xref:System.Globalization.CultureInfo> ilişkili geçerli kültür, giriş dizesini ayrıştıramıyor bir <xref:System.FormatException> oluşturulur.

> [!TIP]
> Tüm C# örnekleri bu makalede, tarayıcınızda çalıştırın. Tuşuna **çalıştırma** çıktıyı görmek için düğme. Ayrıca, bunları kendiniz denemek için de düzenleyebilirsiniz.

> [!NOTE]
> Bu örneklerin her ikisi için de GitHub docs deposuna kullanılabilir [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) ve [VB](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Veya proje için bir zipfile olarak indirebileceğiniz [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) veya [VB](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Bir dizeyi ayrıştırmak biçimlendirme kuralları kullanılır kültürü açıkça de tanımlayabilirsiniz. Standart birini belirtin <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Aşağıdaki örnek, Alman bir dizeye ayrıştırmak için bir biçim sağlayıcısı kullanır. bir <xref:System.DateTime>. Oluşturur bir <xref:System.Globalization.CultureInfo> temsil eden `de-DE` kültür. Olduğunu `CultureInfo` nesne başarılı belirli bu dizenin ayrıştırma sağlar. Bu ayar ne olursa olsun ışığının <xref:System.Threading.Thread.CurrentCulture> , <xref:System.Threading.Thread.CurrentThread>.  
  
[!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Ancak, aşırı yüklemesini kullanmanız mümkün olmakla birlikte <xref:System.DateTime.Parse%2A> yöntemi özel biçim sağlayıcıları belirtmek için standart biçimler ayrıştırma yöntemini desteklemiyor. Bir tarih ve saat standart bir biçimde ifade ayrıştırma için kullanın <xref:System.DateTime.ParseExact%2A> yöntemi yerine.  

<a name="styles-example"></a>Aşağıdaki örnekte <xref:System.Globalization.DateTimeStyles> geçerli tarih ve saat bilgilerini için eklenmemesi gerektiğini belirtmek için numaralandırma <xref:System.DateTime> belirtilmeyen alanları için.  

[!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Yöntemi bir dizeye dönüştürür bir <xref:System.DateTime> , belirtilen dizeyi desenlerden birini için uygun olup nesne. Belirtilen biçimlerden olmayan bir dize bu yönteme geçildiğinde bir <xref:System.FormatException> oluşturulur. Bir standart tarih ve saat biçim belirticisi veya özel biçim belirleyicilerinin bir birleşimi belirtebilirsiniz. Özel biçim belirticileri kullanma, bir özel tanıma dizesi oluşturmak için mümkündür. Tanımlayıcıları açıklaması için üzerinde konulara bakın. [standart tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md).  

Aşağıdaki örnekte, <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi geçirilen ayrıştırmak için bir dize nesnesi tarafından izlenen bir biçim belirtici, ardından bir <xref:System.Globalization.CultureInfo> nesne. Bu <xref:System.DateTime.ParseExact%2A> yöntemi yalnızca uzun tarih düzenini izleyerek dizeleri ayrıştırma `en-US` kültür.  

[!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Her aşırı yüklemesini <xref:System.DateTime.Parse%2A> ve <xref:System.DateTime.ParseExact%2A> yöntemleri de sahip bir <xref:System.IFormatProvider> biçimlendirme dizenin kültüre özgü bilgiler sağlayan bir parametre. Bu <xref:System.IFormatProvider> nesnesi bir <xref:System.Globalization.CultureInfo> bir standart kültürü temsil eden bir nesne veya <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği.  <xref:System.DateTime.ParseExact%2A> bir ek dize veya bir veya daha fazla özel tarih ve saat tanımlayan dize dizisi bağımsız değişkeni de kullanır biçimleri.  

## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Ayrıştırma](parsing-strings.md)
- [Biçimlendirme Türleri](formatting-types.md)
- [.NET içinde Tür Dönüştürme](type-conversion.md)
- [Standart tarih ve saat biçimleri](standard-date-and-time-format-strings.md)
- [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
