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
ms.openlocfilehash: e17b32131e6abc1dba8126799281206f02d46d35
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278187"
---
# <a name="converting-times-between-time-zones"></a>Saatleri saat dilimleri arasında dönüştürme

Zaman dilimleri arasındaki farkları işlemek için tarih ve saatlerle birlikte çalışarak tüm uygulamalar için giderek daha fazla önemli hale gelir. Bir uygulama, her saatin, yapıdan kullanılabilen zaman olan yerel saat içinde ifade edilebilir olduğunu varsaymaz <xref:System.DateTime> . Örneğin, Birleşik Devletler Doğu bölümünde geçerli zamanı görüntüleyen bir Web sayfası Doğu Asya 'daki bir müşteriye karşı güvenilirlik vermez. Bu konuda, saatlerin bir saat diliminden diğerine nasıl dönüştürüleceği ve <xref:System.DateTimeOffset> sınırlı saat dilimi tanıma olan değerlerin nasıl dönüştürüleceği açıklanmaktadır.

## <a name="converting-to-coordinated-universal-time"></a>Eşgüdümlü Evrensel saate dönüştürme

Eşgüdümlü Evrensel Saat (UTC), yüksek duyarlıklı, atomik bir süre standardıdır. Dünyanın saat dilimleri UTC 'den pozitif veya negatif uzaklık olarak ifade edilir. Bu nedenle UTC, bir tür saat dilimi boş veya saat dilimi nötr saati sağlar. Tarih ve saatin bilgisayarlar arasında taşınabilirliği önemli olduğunda UTC zamanının kullanılması önerilir. (Ayrıntılar ve Tarih ve saatleri kullanan diğer en iyi uygulamalar için bkz. [.NET Framework tarih saat kullanarak en iyi yöntemleri kodlama](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) Bağımsız bir saat dilimini UTC 'ye dönüştürmek, zaman karşılaştırmaları kolaylaştırır.

> [!NOTE]
> Ayrıca, bir <xref:System.DateTimeOffset> yapının zaman içinde tek bir noktayı göstermek için bir yapıyı seri hale getirebilirsiniz. <xref:System.DateTimeOffset>Nesneler bir tarih ve saat DEĞERINI UTC 'deki uzaklığa göre depolarsa, UTC ile ilişki içinde her zaman belirli bir noktayı temsil eder.

Bir saati UTC 'ye dönüştürmenin en kolay yolu `static` ( `Shared` Visual Basic) metodunu çağırmanız <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> . Yöntemi tarafından gerçekleştirilen tam dönüştürme, `dateTime` <xref:System.DateTime.Kind%2A> Aşağıdaki tabloda gösterildiği gibi parametrenin özelliğinin değerine bağlıdır.

| `DateTime.Kind`            | Dönüştürme                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Yerel saati UTC 'ye dönüştürür.                                                    |
| `DateTimeKind.Unspecified` | `dateTime`Parametrenin yerel saat olduğunu varsayar ve yerel saatı UTC 'ye dönüştürür. |
| `DateTimeKind.Utc`         | `dateTime`Parametreyi değiştirilmemiş olarak döndürür.                                    |

Aşağıdaki kod geçerli yerel saati UTC 'ye dönüştürür ve sonucu konsola görüntüler.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Tarih ve saat değeri yerel saati veya UTC 'yi temsil etmez, <xref:System.DateTime.ToUniversalTime%2A> Yöntem muhtemelen hatalı bir sonuç döndürür. Ancak, <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> belirli bir saat diliminden tarih ve saati dönüştürmek için yöntemini kullanabilirsiniz. (Hedef saat dilimini temsil eden bir nesneyi alma hakkında daha fazla bilgi için <xref:System.TimeZoneInfo> , bkz. [yerel bir sistemde tanımlanan saat dilimlerini bulma](finding-the-time-zones-on-local-system.md).) Aşağıdaki kod, <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> Doğu Standart SAATINI UTC 'ye dönüştürmek için yöntemini kullanır.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Bu yöntemin, <xref:System.ArgumentException> <xref:System.DateTime> nesnenin <xref:System.DateTime.Kind%2A> özelliği ve saat dilimi yanlış olursa bir oluşturur. <xref:System.DateTime.Kind%2A>Özellik, <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ancak <xref:System.TimeZoneInfo> nesne yerel saat dilimini temsil etmediği ya da <xref:System.DateTime.Kind%2A> özellik ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ancak <xref:System.TimeZoneInfo> nesne eşit değilse <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType> bir uyumsuzluk oluşur.

Bu yöntemlerin hepsi <xref:System.DateTime> değerleri parametre olarak alır ve bir değer döndürür <xref:System.DateTime> . <xref:System.DateTimeOffset>Değerler için, <xref:System.DateTimeOffset> yapının <xref:System.DateTimeOffset.ToUniversalTime%2A> geçerli örneğin TARIH ve saatini UTC 'ye dönüştüren bir örnek yöntemi vardır. Aşağıdaki örnek, <xref:System.DateTimeOffset.ToUniversalTime%2A> yerel bir saati ve diğer birkaç saati Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürmek için yöntemini çağırır.

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>UTC 'yi belirlenen saat dilimine dönüştürme

UTC 'yi yerel saate dönüştürmek için, aşağıdaki "UTC 'den yerel saate dönüştürme" bölümüne bakın. UTC 'yi belirleyeceğiniz herhangi bir zaman diliminde saate dönüştürmek için <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> yöntemini çağırın. Yöntemi iki parametre alır:

- Dönüştürülecek UTC. Bu <xref:System.DateTime> <xref:System.DateTime.Kind%2A> , özelliği veya olarak ayarlanmış bir değer olmalıdır `Unspecified` `Utc` .

- UTC 'nin dönüştürüleceği saat dilimi.

Aşağıdaki kod UTC 'yi orta standart saate dönüştürür.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>UTC 'yi yerel saate dönüştürme

UTC 'yi yerel saate dönüştürmek için <xref:System.DateTime.ToLocalTime%2A> dönüştürmek istediğiniz nesnenin yöntemini çağırın <xref:System.DateTime> . Yönteminin tam davranışı <xref:System.DateTime.Kind%2A> , aşağıdaki tabloda gösterildiği gibi nesnenin özelliğinin değerine bağlıdır.

| `DateTime.Kind`            | Dönüştürme                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | <xref:System.DateTime>Değeri değiştirilmemiş olarak döndürür.                                      |
| `DateTimeKind.Unspecified` | <xref:System.DateTime>DEĞERIN UTC olduğunu varsayar ve UTC 'yi yerel saate dönüştürür. |
| `DateTimeKind.Utc`         | <xref:System.DateTime>Değeri yerel saate dönüştürür.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType>Yöntemi yöntemiyle aynı şekilde davranır `DateTime.ToLocalTime` . Dönüştürülecek tarih ve saat değeri olan tek bir parametre alır.

Ayrıca, `static` ( `Shared` Visual Basic) metodunu kullanarak belirlenen saat diliminizdeki süreyi yerel saate dönüştürebilirsiniz <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> . Bu teknik, sonraki bölümde ele alınmıştır.

## <a name="converting-between-any-two-time-zones"></a>İki saat dilimi arasında dönüştürme

Sınıfının aşağıdaki iki `static` ( `Shared` Visual Basic) yöntemlerinden birini kullanarak iki saat dilimi arasında dönüştürme yapabilirsiniz <xref:System.TimeZoneInfo> :

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Bu yöntemin parametreleri, dönüştürülecek tarih ve saat değeri, `TimeZoneInfo` Tarih ve saat değerinin saat dilimini temsil eden bir nesne ve `TimeZoneInfo` Tarih ve saat değerini dönüştürmek için saat dilimini temsil eden bir nesnedir.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Bu yöntemin parametreleri, dönüştürülecek tarih ve saat değeri, tarih ve saat değerinin saat diliminin tanımlayıcısı ve Tarih ve saat değerinin olarak dönüştürülecek saat diliminin tanımlayıcısıdır.

Her iki yöntem de, <xref:System.DateTime.Kind%2A> dönüştürülecek tarih ve saat değerinin ve <xref:System.TimeZoneInfo> saat dilimini temsil eden nesne ya da saat dilimi tanımlayıcısının bir diğerine karşılık geldiğini gerektirir. Aksi takdirde, bir oluşturulur <xref:System.ArgumentException> . Örneğin, `Kind` Tarih ve saat değerinin özelliği ise `DateTimeKind.Local` , `TimeZoneInfo` yöntemine parametre olarak geçirilen nesne değerine eşit değilse bir özel durum oluşturulur `TimeZoneInfo.Local` . Yöntemine parametre olarak geçirilen tanımlayıcı değerine eşit değilse de bir özel durum oluşturulur `TimeZoneInfo.Local.Id` .

Aşağıdaki örnek, <xref:System.TimeZoneInfo.ConvertTime%2A> Haian standart saatinden yerel saate dönüştürmek için yöntemini kullanır.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>DateTimeOffset değerlerini dönüştürme

Nesneler tarafından temsil edilen tarih ve saat değerleri, <xref:System.DateTimeOffset> nesne, oluşturulduğu sırada saat dilimiyle ilişkili olmadığından tam zaman dilimi farkında değildir. Ancak çoğu durumda, bir uygulamanın bir tarih ve saati belirli saat dilimlerindeki zaman yerine UTC 'den iki farklı uzaklığa göre dönüştürmesi gerekir. Bu dönüştürmeyi gerçekleştirmek için geçerli örnek <xref:System.DateTimeOffset.ToOffset%2A> yöntemini çağırabilirsiniz. Metodun tek parametresi, yöntemin döndürülecek yeni tarih ve saat değerinin bir denkleştirilir.

Örneğin, bir Web sayfası için Kullanıcı isteğinin tarih ve saati biliniyorsa ve aa/gg/yyyy HH: mm: ss zzzz biçiminde bir dize olarak serileştirildiğinde, aşağıdaki `ReturnTimeOnServer` Yöntem bu tarih ve saat değerini Web sunucusundaki tarih ve saate dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)]

Yöntem UTC 'den beş saat dilimde tarih ve saati bir kez geçir9/1/2007 5:32:07 -05:00 Tiyse, ABD Pasifik standart saat diliminde bulunan bir sunucu için 9/1/2007 3:32:07 ÖÖ-07:00 döndürür.

<xref:System.TimeZoneInfo>Sınıfı, <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> zaman dilimi dönüştürmelerini değerlerle gerçekleştiren yönteminin bir aşırı yüklemesini de içerir <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> . Metodun parametreleri bir <xref:System.DateTimeOffset> değerdir ve zaman dilimine bir başvurudur ve bu da zamanın dönüştürülecek olan bir başvurudur. Yöntem çağrısı bir değer döndürür <xref:System.DateTimeOffset> . Örneğin, `ReturnTimeOnServer` önceki örnekteki yöntemi yöntemi çağırmak için aşağıdaki şekilde yeniden yazılabilir <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> .

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.TimeZoneInfo>
- [Tarihler, saatler ve saat dilimleri](index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](finding-the-time-zones-on-local-system.md)
