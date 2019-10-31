---
title: 'Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 2e3a58ffe8332e0afec62461f6897d673e1da09f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131999"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri

Birçok uygulamada, bir tarih ve saat değeri, bir zamanda tek bir noktayı kesin bir şekilde tanımlamak için tasarlanmıştır. Bu konuda, geri yüklenen değerin kaydedilen değerle aynı zamanı tanımladığı şekilde, bir <xref:System.DateTime> değerini, bir <xref:System.DateTimeOffset> değerini ve saat dilimi bilgileriyle tarih ve saat değerlerini kaydetme ve geri yükleme işlemlerinin nasıl yapılacağı gösterilmektedir.

### <a name="to-round-trip-a-datetime-value"></a>Bir DateTime değerini gidiş dönüşlü hale getirmek için

1. <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metodunu "o" biçim belirticisiyle çağırarak <xref:System.DateTime> değerini dize gösterimine dönüştürün.

2. <xref:System.DateTime> değerin dize gösterimini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırında geçirin.

3. <xref:System.DateTime> değerini temsil eden dizeyi alın.

4. <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> `styles` parametresinin değeri olarak geçirin.

Aşağıdaki örnek, bir <xref:System.DateTime> değerini nasıl yuvarlayacağını gösterir.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<xref:System.DateTime> bir değeri yuvarlayıp, bu teknik tüm yerel ve evrensel zamanlar için saati başarıyla korur. Örneğin, yerel bir <xref:System.DateTime> değeri ABD Pasifik standart saat dilimindeki bir sisteme kaydedilirse ve ABD Orta standart saat dilimindeki bir sisteme geri yüklenirse, geri yükleme tarihi ve saati özgün saatten iki saat sonra olur iki saat dilimi arasındaki zaman farkını yansıtan. Ancak, bu teknik belirtilmeyen süreler için doğru değildir. <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified> olan tüm <xref:System.DateTime> değerleri, yerel saatmiş gibi davranır. Böyle bir durum söz konusu değilse, <xref:System.DateTime> doğru zaman noktasını başarıyla tanımmaz. Bu sınırlamanın geçici çözümü, kaydetme ve geri yükleme işlemi için saat dilimiyle birlikte bir tarih ve saat değeri sıkı bir şekilde bir tarih ve saat değerine sahiptir.

### <a name="to-round-trip-a-datetimeoffset-value"></a>Bir DateTimeOffset değerini gidiş dönüşlü hale getirmek için

1. <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodunu "o" biçim belirticisiyle çağırarak <xref:System.DateTimeOffset> değerini dize gösterimine dönüştürün.

2. <xref:System.DateTimeOffset> değerin dize gösterimini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırında geçirin.

3. <xref:System.DateTimeOffset> değerini temsil eden dizeyi alın.

4. <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> `styles` parametresinin değeri olarak geçirin.

Aşağıdaki örnek, bir <xref:System.DateTimeOffset> değerini nasıl yuvarlayacağını gösterir.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Bu teknik her zaman kesin olarak bir <xref:System.DateTimeOffset> değerini tek bir zaman noktası olarak tanımlar. Bu değer daha sonra <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi çağırarak Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürülebilir veya <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> veya <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi çağırarak belirli bir saat dilimindeki zamana dönüştürülebilirler. Bu tekniğin önemli sınırlaması, belirli bir saat dilimindeki süreyi temsil eden bir <xref:System.DateTimeOffset> değeri üzerinde gerçekleştirildiğinde tarih ve saat aritmetiği bu saat dilimi için doğru sonuçlar üretmeyebilir. Bunun nedeni, <xref:System.DateTimeOffset> bir değeri örneklendirilirken, onun saat diliminden bir ilişkisi olmasından kaynaklanır. Bu nedenle, tarih ve saat hesaplamaları gerçekleştirirken bu saat diliminin ayarlama kuralları artık uygulanabilir değildir. Hem tarih hem de saat değeri ile buna eşlik eden saat dilimini içeren özel bir tür tanımlayarak bu soruna geçici bir çözüm bulabilirsiniz.

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Bir tarih ve saat değerini kendi saat dilimiyle gidiş dönüşlü hale getirmek için

1. İki alan içeren bir sınıf veya yapı tanımlayın. İlk alan bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesnesidir ve ikincisi bir <xref:System.TimeZoneInfo> nesnesidir. Aşağıdaki örnek bu tür bir türün basit bir sürümüdür.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Sınıfı <xref:System.SerializableAttribute> özniteliğiyle işaretleyin.

3. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> yöntemi kullanılarak nesneyi seri hale getirme.

4. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> yöntemi kullanarak nesneyi geri yükleyin.

5. Seri durumdan çıkarılan C#nesneyi uygun türdeki bir nesneye atama (ın) veya dönüştürme (Visual Basic).

Aşağıdaki örnek hem tarih hem de saat ve saat dilimi bilgilerini depolayan bir nesneyi nasıl yuvarlayacağını gösterir.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Bu teknik, Birleşik tarih ve saat ve saat dilimi nesnesinin uygulanması tarih değerinin ile eşitlenmemiş hale gelmesine izin vermediğinden, her zaman hem ve sonra hem de kaydedildikten ve geri yüklendikten sonra doğru zaman noktasını yansıtmalıdır. Saat dilimi değeri.

## <a name="compiling-the-code"></a>Kod Derleniyor

Bu örneklerde şunlar gerekir:

- Aşağıdaki ad alanları `using` deyimlerle veya C# Visual Basic `Imports` deyimleriyle içeri aktarılmalıdır:

  - <xref:System> (C# yalnızca).

  - <xref:System.Globalization?displayProperty=nameWithType>.

  - <xref:System.IO?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.

- `DateInTimeZone` sınıfından başka her kod örneği, yöntemlere kaydırılmış ve `Main` yönteminden çağrılan bir sınıfa veya Visual Basic modülüne eklenmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
