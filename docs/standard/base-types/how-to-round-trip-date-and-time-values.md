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
ms.openlocfilehash: 4fc38b6b852f8a7b8f268fd9e8624bdf350744c8
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523816"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri

Birçok uygulamada, bir tarih ve saat değeri, zaman içinde tek bir noktayı kesin olarak tanımlamak için tasarlanmıştır. Bu konu, geri yüklenen <xref:System.DateTime> değerin <xref:System.DateTimeOffset> kaydedilen değerle aynı zamanı tanımlaması için saat dilimi bilgileriyle bir değeri, değeri ve tarih ve saat değerini nasıl kaydedip geri yükleyeceklerini gösterir.

## <a name="round-trip-a-datetime-value"></a>Gidiş-dönüş bir DateTime değeri

1. Yöntemi <xref:System.DateTime> "o" biçim belirtimi ile çağırarak değeri dize gösterimine dönüştürün. <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>

2. Değerin dize <xref:System.DateTime> temsilini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırı boyunca geçirin.

3. Değeri temsil eden <xref:System.DateTime> dizeyi alın.

4. Yöntemi <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametrenin `styles` değeri olarak geçirin.

Aşağıdaki örnekte, bir <xref:System.DateTime> değerin gidiş-dönüş nasıl yapılacağını gösterin.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Bir <xref:System.DateTime> değeri yuvarlattığında, bu teknik tüm yerel ve evrensel zamanlar için zamanı başarıyla korur. Örneğin, yerel <xref:System.DateTime> bir değer ABD Pasifik Standart Saat dilimindeki bir sisteme kaydedilir ve ABD Merkezi Standart Saat dilimindeki bir sistemde geri yüklenirse, geri yüklenen tarih ve saat, iki saat dilimi arasındaki saat farkını yansıtan özgün saatten iki saat sonra olur. Ancak, bu teknik mutlaka belirtilmeyen kez doğru değildir. Özelliği <xref:System.DateTime> yerel <xref:System.DateTime.Kind%2A> zamanlarmış gibi kabul <xref:System.DateTimeKind.Unspecified> edilen tüm değerler. Bu durumda değilse, <xref:System.DateTime> başarıyla zaman içinde doğru noktası tanımlamak olmaz. Bu sınırlama için geçici çözüm sıkıca kaydetmek ve işlemi geri yüklemek için saat dilimi ile bir tarih ve saat değeri çift etmektir.

## <a name="round-trip-a-datetimeoffset-value"></a>Gidiş-dönüş bir DateTimeOffset değeri

1. Yöntemi <xref:System.DateTimeOffset> "o" biçim belirtimi ile çağırarak değeri dize gösterimine dönüştürün. <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>

2. Değerin dize <xref:System.DateTimeOffset> temsilini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırı boyunca geçirin.

3. Değeri temsil eden <xref:System.DateTimeOffset> dizeyi alın.

4. Yöntemi <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametrenin `styles` değeri olarak geçirin.

Aşağıdaki örnekte, bir <xref:System.DateTimeOffset> değerin gidiş-dönüş nasıl yapılacağını gösterin.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Bu teknik her zaman <xref:System.DateTimeOffset> bir değeri zaman içinde tek bir nokta olarak kesin olarak tanımlar. Değer daha sonra <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi çağırarak Eşgüdümlü Evrensel Saat'e (UTC) dönüştürülebilir veya belirli bir saat dilimindeki <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> saate veya yönteme çağrılarek dönüştürülebilir. Bu tekniğin en önemli sınırlaması, belirli bir saat dilimindeki zamanı temsil eden bir <xref:System.DateTimeOffset> değer üzerinde gerçekleştirilen tarih ve saat aritmetik, o saat dilimi için doğru sonuçlar üretemeyebilir. Bunun nedeni, <xref:System.DateTimeOffset> bir değer anında olduğunda, saat diliminden kopuk olmasıdır. Bu nedenle, tarih ve saat hesaplamaları gerçekleştirirken bu saat diliminin ayarlama kuralları artık uygulanamaz. Hem tarih hem de saat değerini ve beraberindeki saat dilimini içeren özel bir tür tanımlayarak bu sorunu çözebilirsiniz.

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a>Saat dilimi ile gidiş-dönüş tarih ve saat değeri

1. İki alaniçeren bir sınıf veya yapı tanımlayın. İlk alan bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesne, ikincisi ise <xref:System.TimeZoneInfo> nesnedir. Aşağıdaki örnek, böyle bir türün basit bir sürümüdür.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Sınıfı öznitelikile <xref:System.SerializableAttribute> işaretleyin.

3. Yöntemi kullanarak nesneyi <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> serileştirin.

4. Yöntemi kullanarak nesneyi geri yükleyin. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>

5. Deserialized nesneyi (C#'da) veya dönüştürme (Visual Basic'te) uygun türdeki bir nesneye dönüştürün.

Aşağıdaki örnek, hem tarih hem de saat dilimi bilgilerini depolayan bir nesneyi nasıl gidiş-dönüş olarak depoladığını göstermektedir.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Bu teknik, birleştirilmiş tarih ve saat ve saat dilimi nesnesinin uygulanmasının tarih değerinin saat dilimi değeriyle eşitlenmemesine izin vermemesi koşuluyla, kaydedilen ve geri yüklendikten sonra doğru zaman noktasını her zaman açık bir şekilde yansıtmalıdır.

## <a name="compile-the-code"></a>Kodu derleme

Bu örnekler şunları gerektirir:

- Aşağıdaki ad alanları C# `using` yönergeleri veya Visual `Imports` Basic deyimleri ile içe aktarılır:

  - <xref:System>(Yalnızca C# )

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- `DateInTimeZone` Sınıf dışındaki her kod örneği, bir sınıfa veya Visual Basic modülüne dahil edilebilir, `Main` yöntemlere sarılmış ve yöntemden çağrılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
