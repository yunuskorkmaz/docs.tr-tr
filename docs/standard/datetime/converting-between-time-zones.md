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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b78e3985169954d71b479aa2e8a034f61afc01
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106959"
---
# <a name="converting-times-between-time-zones"></a>Saatleri saat dilimleri arasında dönüştürme

Zaman dilimleri arasındaki farkları işlemek için tarih ve saatlerle birlikte çalışarak tüm uygulamalar için giderek daha fazla önemli hale gelir. Bir uygulama, her saatin, <xref:System.DateTime> yapıdan kullanılabilen zaman olan yerel saat içinde ifade edilebilir olduğunu varsaymaz. Örneğin, Birleşik Devletler Doğu bölümünde geçerli zamanı görüntüleyen bir Web sayfası Doğu Asya 'daki bir müşteriye karşı güvenilirlik vermez. Bu konuda, saatlerin bir saat diliminden diğerine nasıl dönüştürüleceği ve sınırlı saat dilimi tanıma olan değerlerin nasıl dönüştürüleceği <xref:System.DateTimeOffset> açıklanmaktadır.

## <a name="converting-to-coordinated-universal-time"></a>Eşgüdümlü Evrensel saate dönüştürme

Eşgüdümlü Evrensel Saat (UTC), yüksek duyarlıklı, atomik bir süre standardıdır. Dünyanın saat dilimleri UTC 'den pozitif veya negatif uzaklık olarak ifade edilir. Bu nedenle UTC, bir tür saat dilimi boş veya saat dilimi nötr saati sağlar. Tarih ve saatin bilgisayarlar arasında taşınabilirliği önemli olduğunda UTC zamanının kullanılması önerilir. (Ayrıntılar ve Tarih ve saatleri kullanan diğer en iyi uygulamalar için bkz. [.NET Framework tarih saat kullanarak en iyi yöntemleri kodlama](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) Bağımsız bir saat dilimini UTC 'ye dönüştürmek, zaman karşılaştırmaları kolaylaştırır.

> [!NOTE]
> Ayrıca, bir yapının zaman <xref:System.DateTimeOffset> içinde tek bir noktayı göstermek için bir yapıyı seri hale getirebilirsiniz. <xref:System.DateTimeOffset> Nesneler bir tarih ve saat değerini UTC 'deki uzaklığa göre depolarsa, UTC ile ilişki içinde her zaman belirli bir noktayı temsil eder.

Bir saati UTC 'ye dönüştürmenin en kolay yolu `static` (`Shared` Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> metodunu çağırmanız. Yöntemi tarafından gerçekleştirilen tam dönüştürme, aşağıdaki tabloda gösterildiği gibi `dateTime` <xref:System.DateTime.Kind%2A> parametrenin özelliğinin değerine bağlıdır.

| `DateTime.Kind`            | Dönüştürme                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Yerel saati UTC 'ye dönüştürür.                                                    |
| `DateTimeKind.Unspecified` | `dateTime` Parametrenin yerel saat olduğunu varsayar ve yerel saati UTC 'ye dönüştürür. |
| `DateTimeKind.Utc`         | `dateTime` Parametreyi değiştirilmemiş olarak döndürür.                                    |

Aşağıdaki kod geçerli yerel saati UTC 'ye dönüştürür ve sonucu konsola görüntüler.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Tarih ve saat değeri yerel saati veya UTC 'yi temsil etmez, <xref:System.DateTime.ToUniversalTime%2A> Yöntem muhtemelen hatalı bir sonuç döndürür. Ancak, belirli bir saat diliminden tarih ve saati dönüştürmek için <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. (Hedef saat dilimini temsil eden <xref:System.TimeZoneInfo> bir nesneyi alma hakkında daha fazla bilgi için, bkz. [yerel bir sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Aşağıdaki kod, Doğu Standart <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> saatini UTC 'ye dönüştürmek için yöntemini kullanır.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Bu yöntemin, <xref:System.ArgumentException> <xref:System.DateTime> nesnenin <xref:System.DateTime.Kind%2A> özelliği ve saat dilimi yanlış olursa bir oluşturur. <xref:System.DateTime.Kind%2A> <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>Özellik, ancak<xref:System.TimeZoneInfo>nesne yerel saat dilimini temsil etmediği ya da özellik ise ancak nesne eşit değilse bir uyumsuzluk oluşur. <xref:System.DateTimeKind.Local?displayProperty=nameWithType>

Bu yöntemlerin hepsi değerleri parametre <xref:System.DateTime> olarak alır ve bir <xref:System.DateTime> değer döndürür. Değerler <xref:System.DateTimeOffset> için <xref:System.DateTimeOffset> , yapının geçerli örneğin tarih ve saatini UTC 'ye dönüştüren bir <xref:System.DateTimeOffset.ToUniversalTime%2A> örnek yöntemi vardır. Aşağıdaki örnek, yerel bir <xref:System.DateTimeOffset.ToUniversalTime%2A> saati ve diğer birkaç saati Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürmek için yöntemini çağırır.

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>UTC 'yi belirlenen saat dilimine dönüştürme

UTC 'yi yerel saate dönüştürmek için, aşağıdaki "UTC 'den yerel saate dönüştürme" bölümüne bakın. UTC 'yi belirleyeceğiniz herhangi bir zaman diliminde saate dönüştürmek için <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> yöntemini çağırın. Yöntemi iki parametre alır:

- Dönüştürülecek UTC. Bu, <xref:System.DateTime.Kind%2A> özelliği veya <xref:System.DateTime> olarak`Utc`ayarlanmış bir değer olmalıdır. `Unspecified`

- UTC 'nin dönüştürüleceği saat dilimi.

Aşağıdaki kod UTC 'yi orta standart saate dönüştürür.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>UTC 'yi yerel saate dönüştürme

UTC 'yi yerel saate dönüştürmek için dönüştürmek istediğiniz <xref:System.DateTime.ToLocalTime%2A> <xref:System.DateTime> nesnenin yöntemini çağırın. Yönteminin tam davranışı, aşağıdaki tabloda gösterildiği gibi nesnenin <xref:System.DateTime.Kind%2A> özelliğinin değerine bağlıdır.

| `DateTime.Kind`            | Dönüştürme                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | <xref:System.DateTime> Değeri değiştirilmemiş olarak döndürür.                                      |
| `DateTimeKind.Unspecified` | <xref:System.DateTime> Değerin UTC olduğunu varsayar ve UTC 'yi yerel saate dönüştürür. |
| `DateTimeKind.Utc`         | <xref:System.DateTime> Değeri yerel saate dönüştürür.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Yöntemi `DateTime.ToLocalTime` yöntemiyle aynı şekilde davranır. Dönüştürülecek tarih ve saat değeri olan tek bir parametre alır.

Ayrıca, `static` (`Shared` Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> metodunu kullanarak belirlenen saat diliminizdeki süreyi yerel saate dönüştürebilirsiniz. Bu teknik, sonraki bölümde ele alınmıştır.

## <a name="converting-between-any-two-time-zones"></a>İki saat dilimi arasında dönüştürme

Sınıfının aşağıdaki iki `static` (`Shared` Visual Basic) yöntemlerinden birini kullanarak iki saat dilimi arasında dönüştürme yapabilirsiniz: <xref:System.TimeZoneInfo>

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Bu yöntemin parametreleri, dönüştürülecek tarih ve saat değeri, `TimeZoneInfo` tarih ve saat değerinin saat dilimini temsil eden bir nesne ve Tarih ve saat değerini dönüştürmek için saat dilimini temsil eden bir `TimeZoneInfo` nesnedir.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Bu yöntemin parametreleri, dönüştürülecek tarih ve saat değeri, tarih ve saat değerinin saat diliminin tanımlayıcısı ve Tarih ve saat değerinin olarak dönüştürülecek saat diliminin tanımlayıcısıdır.

Her iki yöntem de, <xref:System.DateTime.Kind%2A> dönüştürülecek tarih ve saat değerinin <xref:System.TimeZoneInfo> ve saat dilimini temsil eden nesne ya da saat dilimi tanımlayıcısının bir diğerine karşılık geldiğini gerektirir. Aksi takdirde, <xref:System.ArgumentException> bir oluşturulur. Örneğin, `Kind` tarih ve saat değerinin özelliği ise `DateTimeKind.Local`, yöntemine `TimeZoneInfo.Local`parametre olarak geçirilen `TimeZoneInfo` nesne değerine eşit değilse bir özel durum oluşturulur. Yöntemine parametre olarak geçirilen tanımlayıcı değerine eşit `TimeZoneInfo.Local.Id`değilse de bir özel durum oluşturulur.

Aşağıdaki örnek, Haian <xref:System.TimeZoneInfo.ConvertTime%2A> standart saatinden yerel saate dönüştürmek için yöntemini kullanır.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>DateTimeOffset değerlerini dönüştürme

Nesneler tarafından <xref:System.DateTimeOffset> temsil edilen tarih ve saat değerleri, nesne, oluşturulduğu sırada saat dilimiyle ilişkili olmadığından tam zaman dilimi farkında değildir. Ancak çoğu durumda, bir uygulamanın bir tarih ve saati belirli saat dilimlerindeki zaman yerine UTC 'den iki farklı uzaklığa göre dönüştürmesi gerekir. Bu dönüştürmeyi gerçekleştirmek için geçerli örnek <xref:System.DateTimeOffset.ToOffset%2A> yöntemini çağırabilirsiniz. Metodun tek parametresi, yöntemin döndürülecek yeni tarih ve saat değerinin bir denkleştirilir.

Örneğin, bir Web sayfası için Kullanıcı isteğinin tarih ve saati biliniyorsa ve aa/gg/yyyy HH: mm: ss zzzz biçiminde bir dize olarak serileştirildiğinde, aşağıdaki `ReturnTimeOnServer` Yöntem bu tarih ve saat değerini Web sunucusundaki tarih ve saate dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Yöntem UTC 'den beş saat dilimde tarih ve saati bir kez geçir9/1/2007 5:32:07 -05:00 Tiyse, ABD 'de bulunan bir sunucu için 9/1/2007 3:32:07 ÖÖ-07:00 döndürür Pasifik standart saat dilimi.

Sınıfı <xref:System.TimeZoneInfo> , zaman dilimi dönüştürmelerini <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> değerlerle gerçekleştiren <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yönteminin bir aşırı yüklemesini de içerir. Metodun parametreleri bir <xref:System.DateTimeOffset> değerdir ve zaman dilimine bir başvurudur ve bu da zamanın dönüştürülecek olan bir başvurudur. Yöntem çağrısı bir <xref:System.DateTimeOffset> değer döndürür. Örneğin, `ReturnTimeOnServer` önceki örnekteki yöntemi <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> yöntemi çağırmak için aşağıdaki şekilde yeniden yazılabilir.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.TimeZoneInfo>
- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
