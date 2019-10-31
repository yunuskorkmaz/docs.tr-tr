---
title: Saatleri saat dilimleri arasında dönüştürme
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
ms.openlocfilehash: d0b38523f054598ba6fb1f05a0183bc4ccff2120
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132559"
---
# <a name="converting-times-between-time-zones"></a>Saatleri saat dilimleri arasında dönüştürme

Zaman dilimleri arasındaki farkları işlemek için tarih ve saatlerle birlikte çalışarak tüm uygulamalar için giderek daha fazla önemli hale gelir. Bir uygulama artık, <xref:System.DateTime> yapısından kullanılabilir olan zaman olan yerel saat içinde her zaman ifade edilebilir olduğunu varsaymaz. Örneğin, Birleşik Devletler Doğu bölümünde geçerli zamanı görüntüleyen bir Web sayfası Doğu Asya 'daki bir müşteriye karşı güvenilirlik vermez. Bu konuda, saatlerin bir saat diliminden diğerine nasıl dönüştürüleceği ve sınırlı saat dilimi tanıma sahip <xref:System.DateTimeOffset> değerlerin nasıl dönüştürüleceği açıklanır.

## <a name="converting-to-coordinated-universal-time"></a>Eşgüdümlü Evrensel saate dönüştürme

Eşgüdümlü Evrensel Saat (UTC), yüksek duyarlıklı, atomik bir süre standardıdır. Dünyanın saat dilimleri UTC 'den pozitif veya negatif uzaklık olarak ifade edilir. Bu nedenle UTC, bir tür saat dilimi boş veya saat dilimi nötr saati sağlar. Tarih ve saatin bilgisayarlar arasında taşınabilirliği önemli olduğunda UTC zamanının kullanılması önerilir. (Ayrıntılar ve Tarih ve saatleri kullanan diğer en iyi uygulamalar için bkz. [.NET Framework tarih saat kullanarak en iyi yöntemleri kodlama](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) Bağımsız bir saat dilimini UTC 'ye dönüştürmek, zaman karşılaştırmaları kolaylaştırır.

> [!NOTE]
> Ayrıca bir <xref:System.DateTimeOffset> yapısını, tek bir zaman noktasını kesin bir şekilde temsil edecek şekilde seri hale getirebilirsiniz. <xref:System.DateTimeOffset> nesneler bir tarih ve saat değerini UTC 'deki uzaklığa göre depolarsa, UTC ile ilişki içinde her zaman belirli bir noktayı temsil eder.

Bir saati UTC 'ye dönüştürmenin en kolay yolu `static` (`Shared` Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> yöntemini çağırmanız. Yöntemi tarafından gerçekleştirilen tam dönüştürme, aşağıdaki tabloda gösterildiği gibi `dateTime` parametresinin <xref:System.DateTime.Kind%2A> özelliğinin değerine bağlıdır.

| `DateTime.Kind`            | Dönüştürme                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Yerel saati UTC 'ye dönüştürür.                                                    |
| `DateTimeKind.Unspecified` | `dateTime` parametresinin yerel saat olduğunu varsayar ve yerel saati UTC 'ye dönüştürür. |
| `DateTimeKind.Utc`         | `dateTime` parametresini değiştirmeden döndürür.                                    |

Aşağıdaki kod geçerli yerel saati UTC 'ye dönüştürür ve sonucu konsola görüntüler.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Tarih ve saat değeri yerel saati veya UTC 'yi temsil etmez, <xref:System.DateTime.ToUniversalTime%2A> Yöntem muhtemelen hatalı bir sonuç döndürür. Ancak, belirli bir saat diliminden tarih ve saati dönüştürmek için <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. (Hedef saat dilimini temsil eden bir <xref:System.TimeZoneInfo> nesnesini alma hakkında daha fazla bilgi için, bkz. [yerel bir sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Aşağıdaki kod, Doğu Standart saatini UTC 'ye dönüştürmek için <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> yöntemini kullanır.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Bu yöntemin, <xref:System.DateTime> nesnesinin <xref:System.DateTime.Kind%2A> özelliği ve saat dilimi uyuşmasından sonra bir <xref:System.ArgumentException> oluşturur. <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, ancak <xref:System.TimeZoneInfo> nesnesi yerel saat dilimini temsil etmediği veya <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, <xref:System.TimeZoneInfo> nesnesi <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>eşit değilse bir uyumsuzluk oluşur.

Bu yöntemlerin hepsi parametre olarak <xref:System.DateTime> değerleri alır ve bir <xref:System.DateTime> değeri döndürür. <xref:System.DateTimeOffset> değerler için, <xref:System.DateTimeOffset> yapısının, geçerli örneğin tarih ve saatini UTC 'ye dönüştüren bir <xref:System.DateTimeOffset.ToUniversalTime%2A> örnek yöntemi vardır. Aşağıdaki örnek, yerel bir saati ve diğer birkaç saati Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürmek için <xref:System.DateTimeOffset.ToUniversalTime%2A> yöntemini çağırır.

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>UTC 'yi belirlenen saat dilimine dönüştürme

UTC 'yi yerel saate dönüştürmek için, aşağıdaki "UTC 'den yerel saate dönüştürme" bölümüne bakın. UTC 'yi belirleyeceğiniz herhangi bir zaman diliminde saate dönüştürmek için <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> yöntemini çağırın. Yöntemi iki parametre alır:

- Dönüştürülecek UTC. Bu, <xref:System.DateTime.Kind%2A> özelliği `Unspecified` veya `Utc`olarak ayarlanmış <xref:System.DateTime> bir değer olmalıdır.

- UTC 'nin dönüştürüleceği saat dilimi.

Aşağıdaki kod UTC 'yi orta standart saate dönüştürür.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>UTC 'yi yerel saate dönüştürme

UTC 'yi yerel saate dönüştürmek için dönüştürmek istediğiniz <xref:System.DateTime> nesnenin <xref:System.DateTime.ToLocalTime%2A> yöntemini çağırın. Yönteminin tam davranışı, aşağıdaki tabloda gösterildiği gibi nesnenin <xref:System.DateTime.Kind%2A> özelliğinin değerine bağlıdır.

| `DateTime.Kind`            | Dönüştürme                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | <xref:System.DateTime> değeri değişmeden döndürür.                                      |
| `DateTimeKind.Unspecified` | <xref:System.DateTime> değerinin UTC olduğunu varsayar ve UTC 'yi yerel saate dönüştürür. |
| `DateTimeKind.Utc`         | <xref:System.DateTime> değerini yerel saate dönüştürür.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> yöntemi `DateTime.ToLocalTime` yöntemiyle aynı şekilde davranır. Dönüştürülecek tarih ve saat değeri olan tek bir parametre alır.

Ayrıca, belirli bir saat dilimindeki süreyi, `static` (Visual Basic`Shared`) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> yöntemi kullanarak yerel saate de dönüştürebilirsiniz. Bu teknik, sonraki bölümde ele alınmıştır.

## <a name="converting-between-any-two-time-zones"></a>İki saat dilimi arasında dönüştürme

<xref:System.TimeZoneInfo> sınıfının aşağıdaki iki `static` (Visual Basic`Shared`) yöntemlerinden birini kullanarak iki saat dilimi arasında dönüştürme yapabilirsiniz:

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Bu yöntemin parametreleri, dönüştürülecek tarih ve saat değeri, tarih ve saat değerinin saat dilimini temsil eden bir `TimeZoneInfo` nesnesi ve Tarih ve saat değerini dönüştürmek için saat dilimini temsil eden bir `TimeZoneInfo` nesnesi.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Bu yöntemin parametreleri, dönüştürülecek tarih ve saat değeri, tarih ve saat değerinin saat diliminin tanımlayıcısı ve Tarih ve saat değerinin olarak dönüştürülecek saat diliminin tanımlayıcısıdır.

Her iki yöntem de, dönüştürülecek tarih ve saat değerinin <xref:System.DateTime.Kind%2A> özelliğinin ve saat dilimini temsil eden <xref:System.TimeZoneInfo> nesne veya saat dilimi tanımlayıcısının birbirine karşılık gelmesini gerektirir. Aksi takdirde, bir <xref:System.ArgumentException> oluşturulur. Örneğin, tarih ve saat değerinin `Kind` özelliği `DateTimeKind.Local`ise, yönteme parametre olarak geçirilen `TimeZoneInfo` nesnesi `TimeZoneInfo.Local`değerine eşit değilse bir özel durum oluşturulur. Yönteme parametre olarak geçirilen tanımlayıcı `TimeZoneInfo.Local.Id`eşitse de bir özel durum oluşturulur.

Aşağıdaki örnek, Haian standart saatinden yerel saate dönüştürmek için <xref:System.TimeZoneInfo.ConvertTime%2A> yöntemini kullanır.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>DateTimeOffset değerlerini dönüştürme

<xref:System.DateTimeOffset> nesneler tarafından temsil edilen tarih ve saat değerleri, nesne, oluşturulduğu sırada saat dilimiyle ilişkili olmadığından, tam zaman dilimi duyarlı değildir. Ancak çoğu durumda, bir uygulamanın bir tarih ve saati belirli saat dilimlerindeki zaman yerine UTC 'den iki farklı uzaklığa göre dönüştürmesi gerekir. Bu dönüştürmeyi gerçekleştirmek için, geçerli örneğin <xref:System.DateTimeOffset.ToOffset%2A> yöntemini çağırabilirsiniz. Metodun tek parametresi, yöntemin döndürülecek yeni tarih ve saat değerinin bir denkleştirilir.

Örneğin, bir Web sayfası için Kullanıcı isteğinin tarih ve saati biliniyorsa ve aa/gg/yyyy HH: mm: ss zzzz biçiminde bir dize olarak serileştirildiğinde aşağıdaki `ReturnTimeOnServer` yöntemi bu tarih ve saat değerini Web sunucusundaki tarih ve saate dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Yöntem UTC 'den beş saat dilimde tarih ve saati bir kez geçir9/1/2007 5:32:07 -05:00 Tiyse, ABD Pasifik standart saat diliminde bulunan bir sunucu için 9/1/2007 3:32:07 ÖÖ-07:00 döndürür.

<xref:System.TimeZoneInfo> sınıfı, <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> değerleriyle saat dilimi dönüştürmeleri gerçekleştiren <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yönteminin bir aşırı yüklemesini de içerir. Metodun parametreleri bir <xref:System.DateTimeOffset> değerdir ve zaman dilimini bir başvurudur ve bu da zaman dilimine dönüştürülür. Yöntem çağrısı <xref:System.DateTimeOffset> bir değer döndürür. Örneğin, önceki örnekteki `ReturnTimeOnServer` yöntemi, <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> yöntemini çağırmak için aşağıdaki şekilde yeniden yazılabilir.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.TimeZoneInfo>
- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
