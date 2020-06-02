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
ms.openlocfilehash: 60483a6e29c65fc0c5803e8084053d53d9fc3c37
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290454"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri

Birçok uygulamada, bir tarih ve saat değeri, bir zamanda tek bir noktayı kesin bir şekilde tanımlamak için tasarlanmıştır. Bu makalede <xref:System.DateTime> , <xref:System.DateTimeOffset> geri yüklenen değerin kaydedilen değerle aynı zamanı tanımladığı şekilde, saat dilimi bilgileriyle bir değerin, bir değerin ve Tarih ve saat değerinin nasıl kaydedileceği ve geri yükleneceği gösterilmektedir.

## <a name="round-trip-a-datetime-value"></a>Bir tarih saat değeri gidiş dönüş

1. <xref:System.DateTime> <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Yöntemi "o" biçim belirticisiyle çağırarak değeri dize gösterimine dönüştürün.

2. Değerin dize gösterimini <xref:System.DateTime> bir dosyaya kaydedin veya bir işlem, uygulama etki alanı ya da makine sınırı üzerinden geçirin.

3. Değeri temsil eden dizeyi alın <xref:System.DateTime> .

4. Yöntemini çağırın <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametresinin değeri olarak geçirin `styles` .

Aşağıdaki örnek, bir değeri nasıl yuvarlayacağını gösterir <xref:System.DateTime> .

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Bir değeri yuvarlayıp <xref:System.DateTime> , bu teknik tüm yerel ve evrensel zamanlar için saati başarıyla korur. Örneğin, yerel bir <xref:System.DateTime> değer ABD Pasifik standart saat dilimindeki bir sisteme kaydedilirse ve ABD Orta standart saat dilimindeki bir sisteme geri yüklenirse, geri yükleme tarihi ve saati, ilk zamandan sonraki iki saat sonra olur ve bu da iki saat dilimi arasındaki zaman farkını yansıtır. Ancak, bu teknik belirtilmeyen süreler için doğru değildir. <xref:System.DateTime> <xref:System.DateTime.Kind%2A> Özelliği <xref:System.DateTimeKind.Unspecified> Yerel saatmiş gibi kabul edilen tüm değerler. Yerel bir zaman değilse, <xref:System.DateTime> doğru zaman noktasını başarıyla tanımlamaz. Bu sınırlamanın geçici çözümü, kaydetme ve geri yükleme işlemi için saat dilimiyle birlikte bir tarih ve saat değeri sıkı bir şekilde bir tarih ve saat değerine sahiptir.

## <a name="round-trip-a-datetimeoffset-value"></a>Bir DateTimeOffset değerini gidiş dönüş

1. <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> Yöntemi "o" biçim belirticisiyle çağırarak değeri dize gösterimine dönüştürün.

2. Değerin dize gösterimini <xref:System.DateTimeOffset> bir dosyaya kaydedin veya bir işlem, uygulama etki alanı ya da makine sınırı üzerinden geçirin.

3. Değeri temsil eden dizeyi alın <xref:System.DateTimeOffset> .

4. Yöntemini çağırın <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametresinin değeri olarak geçirin `styles` .

Aşağıdaki örnek, bir değeri nasıl yuvarlayacağını gösterir <xref:System.DateTimeOffset> .

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Bu teknik her zaman, bir <xref:System.DateTimeOffset> değeri bir zaman içinde tek bir noktaya kadar kesin olarak tanımlar. Bu değer, yöntemi çağırarak Eşgüdümlü Evrensel saate (UTC) dönüştürülebilir <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> veya ya da yöntemi çağırarak belirli bir saat dilimindeki zamana dönüştürülebilir <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> . Bu tekniğin önemli sınırlaması, belirli bir saat dilimindeki süreyi temsil eden bir değer üzerinde gerçekleştirildiğinde tarih ve saat aritmetiği bu <xref:System.DateTimeOffset> saat dilimi için doğru sonuçlar üretmeyebilir. Bunun nedeni, bir <xref:System.DateTimeOffset> değer örneklendirilirken, onun saat diliminden bir ilişkisi olmasından kaynaklanır. Bu nedenle, tarih ve saat hesaplamaları gerçekleştirirken bu saat diliminin ayarlama kuralları artık uygulanabilir değildir. Hem tarih hem de saat değeri ile buna eşlik eden saat dilimini içeren özel bir tür tanımlayarak bu soruna geçici bir çözüm bulabilirsiniz.

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a>Tarih ve saat değerini saat dilimiyle gidiş dönüş

1. İki alan içeren bir sınıf veya yapı tanımlayın. İlk alan bir <xref:System.DateTime> ya da bir <xref:System.DateTimeOffset> nesnedir ve ikincisi bir <xref:System.TimeZoneInfo> nesnedir. Aşağıdaki örnek bu tür bir türün basit bir sürümüdür.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Sınıfı özniteliği ile işaretleyin <xref:System.SerializableAttribute> .

3. Yöntemini kullanarak nesneyi seri hale getirme <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> .

4. Yöntemini kullanarak nesneyi geri yükleyin <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> .

5. Atama (C#) veya seri durumdan çıkarılan nesneyi uygun türdeki bir nesneye (Visual Basic) dönüştürün.

Aşağıdaki örnek, hem saat dilimini hem de tarih ve saat bilgilerini depolayan bir nesneyi nasıl yuvarlayacağını gösterir.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Bu teknik, Birleşik tarih ve saat ve saat dilimi nesnesinin uygulanması tarih değerinin saat dilimi değeriyle eşitlenmesine izin vermediğinden, her zaman hem ve sonra hem de sonrasında doğru zaman noktasını yansıtmalıdır.

## <a name="compile-the-code"></a>Kodu derle

Bu örnekler şunları gerektirir:

- Aşağıdaki ad alanları C# `using` yönergeleri veya Visual Basic deyimleri ile içeri aktarılır `Imports` :

  - <xref:System>(Yalnızca C#)

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- Sınıf dışındaki her kod örneği, `DateInTimeZone` metotlara kaydırılmış bir sınıfa veya Visual Basic modüle dahil edilir ve `Main` yönteminden çağırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../datetime/choosing-between-datetime.md)
- [Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md)
