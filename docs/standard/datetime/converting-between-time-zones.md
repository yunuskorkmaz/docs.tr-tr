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
ms.openlocfilehash: 0c77832a4c578ddb2c8a427b133e53ab4ab5c5e3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529590"
---
# <a name="converting-times-between-time-zones"></a>Saatleri saat dilimleri arasında dönüştürme

Tarihleri ve saatleri saat dilimleri arasındaki farklar işlemek için çalışan herhangi bir uygulama için giderek daha çok önem kazanmaktadır. Bir uygulama, her zaman ifade edilemez yerel saatle artık kabul edilebilir olduğu zaman kullanılabilir <xref:System.DateTime> yapısı. Örneğin, Amerika Birleşik Devletleri Doğu parçası geçerli saati gösteren bir Web sayfası güvenilirlik Doğu Asya müşteriye eksik. Bu konu, saatler bir saat diliminden dönüştürme yanı sıra nasıl dönüştürüleceğini açıklar <xref:System.DateTimeOffset> saat dilimini tanıma sınırlı değerler.

## <a name="converting-to-coordinated-universal-time"></a>Dönüştürme için Eşgüdümlü Evrensel Saat

Eşgüdümlü Evrensel Saat (UTC) bir yüksek duyarlıklı, atomik standart zamandır. Dünyanın saat dilimi UTC pozitif veya negatif uzaklık olarak ifade edilir. Bu nedenle, UTC saat dilimi boş veya saat dilimi bağımsız zaman bir türünü sağlar. UTC saati bir tarih zaman önerilir ve saatin taşınabilirlik bilgisayarlardaki önemlidir. (Ayrıntıları ve tarihler ve saatler kullanarak diğer en iyi yöntemler için bkz: [en iyi uygulamaları .NET Framework'DateTime ' ı kullanarak kodlama](https://msdn.microsoft.com/library/ms973825.aspx).) Tek tek saat dilimlerini UTC'ye dönüştürme zaman karşılaştırmalar kolaylaştırır.

> [!NOTE]
> Ayrıca serileştirebilen bir <xref:System.DateTimeOffset> yapısı tek bir noktadan zaman içinde kesin bir şekilde göstermek için. Çünkü <xref:System.DateTimeOffset> nesneleri depolamak bir tarih ve saat değerini utc'den uzaklığı yanı sıra, her zaman belirli bir noktaya ilişki zamanın UTC'ye temsil ederler.

UTC'ye dönüştürün en kolay yolu çağırmaktır `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> yöntemi. Yöntem tarafından gerçekleştirilen tam dönüştürme değerine bağlıdır `dateTime` parametrenin <xref:System.DateTime.Kind%2A> özelliği, aşağıdaki tabloda gösterildiği gibi.

| `DateTime.Kind`            | Dönüştürme                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Yerel saat UTC'ye dönüştürür.                                                    |
| `DateTimeKind.Unspecified` | Varsayar `dateTime` parametredir yerel saat ve UTC yerel saate dönüştürür. |
| `DateTimeKind.Utc`         | Döndürür `dateTime` değişmeden parametresi.                                    |

Aşağıdaki kod, geçerli yerel saat UTC'ye dönüştürür ve sonuç konsolda görüntüler.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> Yöntemi aynıdır sonuçları mutlaka oluşturmuyor <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType> ve <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> yöntemleri. Konak sisteminin yerel saat dilimi birden çok ayarlama kuralları içerir <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> uygun kural belirli bir tarih ve saat için geçerlidir. Diğer iki yöntem her zaman en son ayarlama kuralı uygulayın.

Yerel saat ya da UTC tarih ve saat değerini temsil etmiyorsa <xref:System.DateTime.ToUniversalTime%2A> yöntemi büyük olasılıkla hatalı bir sonuç döndürür. Ancak, kullanabileceğiniz <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> tarihi ve saati belirtilen bir saat diliminden dönüştürmek için yöntemi. (Ayrıntılı bilgi almak için bir <xref:System.TimeZoneInfo> hedef saat dilimini temsil eden nesneyi görmek [yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Aşağıdaki kod <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> Doğu Standart Saati UTC'ye dönüştürmek için yöntemi.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Bu yöntem Not bir <xref:System.ArgumentException> varsa <xref:System.DateTime> nesnenin <xref:System.DateTime.Kind%2A> özellik ve saat dilimini eşleşmiyor. Bir uyuşmazlık varsa ortaya <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ancak <xref:System.TimeZoneInfo> nesnesi, yerel saat dilimini temsil etmiyor veya <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ancak <xref:System.TimeZoneInfo> nesnesi eşit değil <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>.

Tüm bu yöntemleri ele <xref:System.DateTime> parametreleri ve dönüş değerlerini bir <xref:System.DateTime> değeri. İçin <xref:System.DateTimeOffset> değerleri <xref:System.DateTimeOffset> yapıya sahip bir <xref:System.DateTimeOffset.ToUniversalTime%2A> örnek tarih ve saati geçerli örneğin UTC'ye dönüştürür yöntemi. Aşağıdaki örnek çağrıları <xref:System.DateTimeOffset.ToUniversalTime%2A> bir yerel saat ile birkaç kez Eşgüdümlü Evrensel Saat (UTC) dönüştürmek için yöntemi.

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>İçin belirlenen bir saat dilimi UTC Dönüştürme

Yerel saat UTC'ye dönüştürmek için aşağıdaki "yerel için UTC saat dönüştürme" bölümüne bakın. Sizin belirlediğiniz bir saat dilimindeki saati UTC'ye dönüştürmek için çağrı <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> yöntemi. Yöntem iki parametre alır:

* Dönüştürülecek UTC. Bu olmalıdır bir <xref:System.DateTime> ayarlanmış değer <xref:System.DateTime.Kind%2A> özelliği `Unspecified` veya `Utc`.

* UTC'ye dönüştürmek için saat dilimi.

Aşağıdaki kodu için merkezi standart saat UTC'ye dönüştürür.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Yerel saat UTC'ye dönüştürme

Yerel saat UTC'ye dönüştürmek için çağrı <xref:System.DateTime.ToLocalTime%2A> yöntemi <xref:System.DateTime> süresi dönüştürmek istediğiniz nesne. Tam davranış yöntemi nesnenin değerine bağlıdır <xref:System.DateTime.Kind%2A> özelliği, aşağıdaki tabloda gösterildiği gibi.

| `DateTime.Kind`            | Dönüştürme                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Döndürür <xref:System.DateTime> değerini değiştirmeden.                                      |
| `DateTimeKind.Unspecified` | Varsayar <xref:System.DateTime> değeri UTC ve yerel saat UTC'ye dönüştürür. |
| `DateTimeKind.Utc`         | Dönüştürür <xref:System.DateTime> yerel saat değeri.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Yöntemi öğesine aynı şekilde davranır `DateTime.ToLocalTime` yöntemi. Dönüştürülecek tarih ve saat değeri olan işlem tek bir parametre alır.

Kullanarak yerel saat olarak belirlenen bir saat dilimindeki saati dönüştürebilirsiniz `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> yöntemi. Bu teknik, sonraki bölümde ele alınmıştır.

## <a name="converting-between-any-two-time-zones"></a>Her iki saat dilimleri arasında dönüştürme

Aşağıdaki iki birini kullanarak her iki saat dilimleri arasında dönüştürme yapabilirsiniz `static` (`Shared` Visual Basic'te) yöntemleri <xref:System.TimeZoneInfo> sınıfı:

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  Bu yöntemin parametre dönüştürmek için tarih ve saat değeri olan bir `TimeZoneInfo` tarih ve saat değerinin saat dilimini temsil eden nesne ve `TimeZoneInfo` tarih ve saat değerine dönüştürmek için bu saat dilimini temsil eden nesne.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Tarih ve saat değerini dönüştürmek için tarih ve saat değerinin saat dilimi tanımlayıcısıdır ve saat dilimi tanımlayıcı tarih ve saat değerine dönüştürmek için bu yöntemin parametre değildir.

Her iki yöntem de gerektiren <xref:System.DateTime.Kind%2A> dönüştürülecek tarih ve saat değeri özelliğine ve <xref:System.TimeZoneInfo> saat dilimini temsil eden nesne veya saat dilimi tanımlayıcı bir başkasına karşılık gelir. Aksi takdirde, bir <xref:System.ArgumentException> oluşturulur. Örneğin, varsa `Kind` tarih ve saat değerinin özelliği `DateTimeKind.Local`, değilse bir özel durum `TimeZoneInfo` yönteme parametre olarak nesne eşit değil `TimeZoneInfo.Local`. Yönteme parametre olarak geçirilen tanımlayıcısı eşit değilse bir özel ayrıca durum `TimeZoneInfo.Local.Id`.

Aşağıdaki örnekte <xref:System.TimeZoneInfo.ConvertTime%2A> gelen Hawaii Standart Saati yerel saate dönüştürme yöntemi.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>DateTimeOffset değer dönüştürme

Tarafından temsil edilen tarih ve saat değerlerini <xref:System.DateTimeOffset> nesneleri tam olarak saat dilimi değildir çünkü nesne kendi saat diliminden zaman noktanızla ilişkisi silinir kullanan örneği oluşturulduğu. Ancak, çoğu durumda uygulama yalnızca bir tarih dönüştürme erişmesi ve zamanı iki farklı uzaklıkları UTC saati yerine özellikle saat dilimlerini tabanlı. Bu dönüştürme gerçekleştirmek için geçerli örneğin çağırabilirsiniz <xref:System.DateTimeOffset.ToOffset%2A> yöntemi. Yöntemin tek döndürmek için yöntemin olan zaman değer ve yeni tarihi uzaklığı parametredir.

Örneğin, bir kullanıcının saat ve tarihi için istemesi durumunda bir Web sayfası denir ve aa/gg/yyyy ss: dd: zzzz, aşağıdaki biçimde bir dize olarak serileştirilmiş `ReturnTimeOnServer` yöntemi, tarih ve saate Web sunucusunda bu tarih ve saat değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Yöntem bir dize iletilmezse "1/9/2007 5:32:07-05: 00" temsil eden tarih ve saat dilimindeki saati UTC'den önceki beş saat, 1/9/2007 döndürür AM 3:32:07 -07:00 ABD'de bulunan bir sunucu için Pasifik Standart saat dilimi.

<xref:System.TimeZoneInfo> Sınıfı da içeren bir aşırı yüklemesini <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> saat dilimi dönüşümleri gerçekleştirir yöntemi <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> değerleri. Yöntemin parametreleri bir <xref:System.DateTimeOffset> değer ve başvuru saati olduğu dönüştürülecek saat dilimi. Yöntem çağrısı döndürür bir <xref:System.DateTimeOffset> değeri. Örneğin, `ReturnTimeOnServer` yöntemi önceki örnekte yazılan şu şekilde çağrılacak <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> yöntemi.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

* <xref:System.TimeZoneInfo>
* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
* [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
