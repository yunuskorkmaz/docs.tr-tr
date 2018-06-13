---
title: 'Nasıl yapılır: dizeleri DateTime olarak dönüştürme'
description: Tarihler ve saatler DateTime tarih ve saat dizesi oluşturmak için temsil eden dizeleri ayrıştırma teknikleri hakkında bilgi edinin.
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
ms.openlocfilehash: 4c093f22f77284d15e56c8f1d4a95afbeb75202d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576109"
---
# <a name="parsing-date-and-time-strings-in-net"></a>Tarih ve saat dizelerini .NET ayrıştırma

Bunları dönüştürmek için dizeleri ayrıştırma <xref:System.DateTime> nesneleri tarihler ve saatler metin olarak nasıl temsil hakkında bilgi belirtmenizi gerektirir. Farklı kültürler farklı siparişleri gün, ay ve yıl için kullanın. Bazı zaman Beyanları 24 saatlik kullanın, diğerleri "AM" ve "PM." belirtin Bazı uygulamalar yalnızca tarih gerekir. Başkalarının yalnızca zaman gerekir. Hala başkalarının tarih ve saat belirtmeniz gerekir. Dizelere dönüştürme yöntemleri <xref:System.DateTime> nesneleri beklediğiniz biçimleri ve tarih öğeleri hakkında ayrıntılı bilgi sağlar ve uygulamanızın gereksinimlerine saat olanak tanır. Doğru metne dönüştürme için üç alt görevler vardır bir <xref:System.DateTime>:

1. Tarih ve saatini temsil eden metin biçimiyle belirtmeniz gerekir.
1. Tarih saat biçimini kültür belirtebilir.
1. Nasıl eksik bileşenlerini belirtebilir metin gösterimi tarih ve saat ayarlanır.

<xref:System.DateTime.Parse%2A> Ve <xref:System.DateTime.TryParse%2A> yöntemleri bir tarih ve saat birçok ortak gösterimlerini Dönüştür. <xref:System.DateTime.ParseExact%2A> Ve <xref:System.DateTime.TryParseExact%2A> yöntemleri bir tarih ve saat biçim dizesi tarafından belirtilen desenle uyan bir dize gösterimi Dönüştür. (Makaleleri bakın [standart tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md) Ayrıntılar için.)


Geçerli <xref:System.Globalization.DateTimeFormatInfo> nesnesi nasıl metin bir tarih ve saat yorumlanması gerektiğini üzerinde daha fazla denetim sağlar. Özelliklerini bir <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat ayırıcılar ve "AM" ve "PM" belirtimler ay, gün ve eras ve biçim adlarının açıklanmaktadır. Geçerli iş parçacığı kültürünü sağlayan bir <xref:System.Globalization.DateTimeFormatInfo> temsil eden geçerli kültür. Belirttiğiniz belirli bir kültür veya özel ayarlar isterseniz, <xref:System.IFormatProvider> ayrıştırma yönteminin parametresi. İçin <xref:System.IFormatProvider> parametresini belirtin bir <xref:System.Globalization.CultureInfo> bir kültür temsil eder, nesne veya <xref:System.Globalization.DateTimeFormatInfo> nesnesi.

Bir tarih veya saat temsil eden metin bazı bilgiler eksik olabilir. Örneğin, çoğu kişi "Mart 12" geçerli yıl temsil eden tarih varsayın. Benzer şekilde, "Mart 2018" Mart 2018 yıl ay temsil eder. Metin genellikle temsil eden saat yalnızca mu saat, dakika ve AM/PM ataması içerir.  Ayrıştırma yöntemleri makul varsayılanları kullanarak bu bilgileri eksik işler:

- Yalnızca mevcut olduğunda, tarih bölümü geçerli tarihi kullanır.
- Yalnızca tarihi mevcut saat bölümü gece yarısı olur.
- Yılın bir tarih belirtilmediğinde, geçerli yıl kullanılır.
- Ayın gününü belirtilmediğinde, ayın ilk kullanılır.

Tarih dizesinde mevcut değilse, ay ve gün veya yıl birini içermelidir. Süresi varsa, saat ve dakika veya AM/PM Belirleyicisi içermelidir.

Belirleyebileceğiniz <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> bu Varsayılanları geçersiz kılmak için sabiti. Kullandığınızda bu sabiti, eksik yıl, ay veya gün özellikleri değerine ayarlanmış `1`. [Son örnek](#styles-example) kullanarak <xref:System.DateTime.Parse%2A> Bu davranış gösterir.

Bir tarih ve saat bileşeni ek olarak, bir tarih ve saat dize gösterimini ne kadar zaman Eşgüdümlü Evrensel Saat (UTC) öğesinden farklı gösteren uzaklığı içerebilir. Örneğin, dize "14/2/2007 5:32:00 -7:00" başka bir deyişle yedi saatler UTC'den önceki bir zaman tanımlar. Uzaklığı bir zaman dize gösterimini atlanırsa döndürür ayrıştırma bir <xref:System.DateTime> nesnesi ile kendi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Bir uzaklık belirtilirse, döndürür ayrıştırma bir <xref:System.DateTime> nesnesi ile kendi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ve değerini makinenizde yerel saat dilimine ayarlanır. Kullanarak bu davranışı değiştirebilirsiniz bir <xref:System.Globalization.DateTimeStyles> ayrıştırma yönteminin değerle.
  
Biçim sağlayıcısı belirsiz bir sayısal tarihi yorumlamak için de kullanılır. Hangi "03/02/04" dizeyle gösterilen tarih ay, gün ve yıl bileşenleridir açık değil. Bileşenleri biçimi sağlayıcısında benzer tarih biçimleri sırasını göre değerlendirilir.

## <a name="parse"></a>Ayrıştırma

Aşağıdaki örnek kullanımını göstermektedir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> dönüştürmek için yöntem bir `string` içine bir <xref:System.DateTime>. Bu örnek, geçerli iş parçacığı ile ilişkili kültür kullanır. Varsa <xref:System.Globalization.CultureInfo> geçerli ilişkili kültür giriş dizesini ayrıştıramıyor bir <xref:System.FormatException> oluşturulur.

> [!TIP]
> Tüm C# örnekleri bu makalede, tarayıcınızda çalıştırın. Tuşuna **çalıştırmak** çıkışı görmek düğmesi. Ayrıca, bunları kendiniz denemeler yapmak için de düzenleyebilirsiniz.

> [!NOTE]
> Bu örnekler GitHub belgeleri depo her ikisi için de kullanılabilir olan [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) ve [VB](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Veya zipfile için olarak proje indirebilirsiniz [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) veya [VB](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Bir dize ayrıştırma, biçimlendirme kuralları kullanılan kültür açıkça tanımlayabilirsiniz. Standart birini belirtin <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Aşağıdaki örnek, Almanca bir dizeye ayrıştırmak için bir biçim sağlayıcısını kullanır. bir <xref:System.DateTime>. Oluşturduğu bir <xref:System.Globalization.CultureInfo> temsil eden `de-DE` kültür. Olduğunu `CultureInfo` başarılı bu belirli dizesini ayrıştırma nesnesi sağlar. Bu ayar ne olursa olsun önleyen <xref:System.Threading.Thread.CurrentCulture> , <xref:System.Threading.Thread.CurrentThread>.  
  
[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Ancak, aşırı kullanabilirsiniz ancak <xref:System.DateTime.Parse%2A> yöntemi özel biçim sağlayıcıları belirtmek için standart olmayan biçimleri ayrıştırma yöntemini desteklemiyor. Bir tarih ve saat standart olmayan bir biçimde ifade ayrıştırmak için kullanmak <xref:System.DateTime.ParseExact%2A> yöntemi yerine.  

<a name="styles-example"></a>Aşağıdaki örnek kullanır <xref:System.Globalization.DateTimeStyles> geçerli tarih ve saat bilgilerini için eklenmemesi gerektiğini belirtmek için numaralandırma <xref:System.DateTime> belirtilmeyen alanlar için.  

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Yöntemi bir dizeye dönüştürür bir <xref:System.DateTime> , belirtilen dizeyi desenleri birine uyup uymadığını nesne. Bu yöntem için belirtilen biçimlerden birini olmayan bir dize geçirildiğinde bir <xref:System.FormatException> oluşturulur. Özel biçim belirticileri bileşimini veya standart tarih ve saat biçim belirticileri birini belirtebilirsiniz. Özel biçim belirticilerini kullanma, sizin için bir özel tanıma dizesi oluşturmak mümkündür. Üzerinde konular tanımlayıcıları açıklaması için bkz [standart tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md).  

Aşağıdaki örnekte, <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi geçirilen ayrıştırmak için bir dize nesnesi ve ardından bir biçim belirticisi arkasından bir <xref:System.Globalization.CultureInfo> nesnesi. Bu <xref:System.DateTime.ParseExact%2A> yöntemi yalnızca uzun tarih desende izleyin dizeleri ayrıştırma `en-US` kültür.  

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Her aşırı yüklemesini <xref:System.DateTime.Parse%2A> ve <xref:System.DateTime.ParseExact%2A> yöntemleri de sahip bir <xref:System.IFormatProvider> biçimlendirme kültüre özgü bilgileri dizesinin sağlar parametresi. Bu <xref:System.IFormatProvider> nesne bir <xref:System.Globalization.CultureInfo> standart bir kültür temsil eden nesnesi veya bir <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği.  <xref:System.DateTime.ParseExact%2A> Ayrıca bir ek bir dize veya bir veya daha fazla özel tarih ve saat tanımlayan dize dizisi bağımsız değişken kullanır biçimleri.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizeleri Ayrıştırma](parsing-strings.md)  
 [Biçimlendirme Türleri](formatting-types.md)  
 [.NET içinde Tür Dönüştürme](type-conversion.md)  
 [Standart tarih ve saat biçimleri](standard-date-and-time-format-strings.md)  
 [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
