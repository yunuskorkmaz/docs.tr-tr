---
title: "Saatleri saat dilimleri arasında dönüştürme"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eabe0c1511e6fd42798f1a879e9e8d526d543a29
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2018
---
# <a name="converting-times-between-time-zones"></a>Saatleri saat dilimleri arasında dönüştürme

Tarih ve saatleri saat dilimleri arasındaki farklar işlemek için birlikte çalışır. herhangi bir uygulama için önemli giderek büyüyor. Bir uygulama, her zaman ifade edilir yerel saatle artık kabul edilebilir olduğu zaman kullanılabilir <xref:System.DateTime> yapısı. Örneğin, geçerli saati Doğu ABD bölümünde görüntüleyen bir Web sayfası, Doğu Asya müşteriye itibarı eksik kalacaktır. Bu konuda nasıl dönüştürüleceği yanı sıra, bir saat dilimine kez dönüştürme açıklanmaktadır <xref:System.DateTimeOffset> saat dilimi tanıma sınırlı değerleri.

## <a name="converting-to-coordinated-universal-time"></a>Eşgüdümlü Evrensel Saat dönüştürme

Eşgüdümlü Evrensel Saat (UTC) bir Yüksek duyarlılık, atomik standart zamandır. Dünyanın saat dilimi UTC gelen olumlu veya olumsuz uzaklıkları olarak ifade edilir. Bu nedenle, UTC saat dilimi boş veya saat dilimi nötr saat tür sağlar. UTC saati tarih zaman önerilir ve bilgisayarlar arasında zaman taşınabilirlik önemlidir. (Ayrıntıları ve tarihler ve saatler kullanarak diğer en iyi yöntemler için bkz: [DateTime .NET Framework kullanarak en iyi yöntemler kodlama](https://msdn.microsoft.com/library/ms973825.aspx).) Tek tek saat dilimleri için UTC Dönüştürme zaman karşılaştırmaları kolaylaştırır.

> [!NOTE]
> Ayrıca serileştirebilen bir <xref:System.DateTimeOffset> yapısı belirsizliğe zamanında tek bir nokta temsil eder. Çünkü <xref:System.DateTimeOffset> nesneleri depolamak tarih ve saat değeri kendi UTC uzaklığı birlikte, bunlar her zaman belirli bir noktaya ilişki zamanında UTC'ye temsil eder.

Bir saat UTC'ye dönüştürmek için en kolay yolu çağırmaktır `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> yöntemi. Yöntemi tarafından gerçekleştirilen tam dönüştürme değerine bağlıdır `dateTime` parametrenin <xref:System.DateTime.Kind%2A> özelliği, aşağıdaki tabloda gösterildiği gibi.

| `DateTime.Kind`            | Dönüştürme                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Yerel saat UTC'ye dönüştürür.                                                    |
| `DateTimeKind.Unspecified` | Varsayar `dateTime` parametredir yerel saat ve yerel saati UTC dönüştürür. |
| `DateTimeKind.Utc`         | Döndürür `dateTime` değişmeden parametresi.                                    |

Aşağıdaki kod, geçerli yerel saat UTC'ye dönüştürür ve konsola sonucu görüntüler.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> Yöntemi olmayan mutlaka sonuçlar özdeş <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType> ve <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> yöntemleri. Ana bilgisayar sistemi yerel saat dilimi birden çok ayarlama kuralları içerir <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> uygun kural belirli bir tarih ve saat için geçerlidir. Diğer iki yöntem her zaman en son ayarlama kuralı uygulanır.

Yerel saat ya da UTC, tarih ve saat değeri temsil etmiyor, <xref:System.DateTime.ToUniversalTime%2A> yöntemi büyük olasılıkla hatalı bir sonuç döndürür. Ancak, kullanabileceğiniz <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> tarih ve saat belirtilen saat diliminden dönüştürmek için yöntem. (Alma ile ilgili ayrıntılar için bir <xref:System.TimeZoneInfo> hedef saat dilimini temsil eden nesneyi görmek [yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Aşağıdaki kod <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> Doğu Standart Saati için UTC dönüştürmek için yöntem.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Bu yöntem oluşturulur Not bir <xref:System.ArgumentException> varsa <xref:System.DateTime> nesnenin <xref:System.DateTime.Kind%2A> özellik ve saat dilimi eşleşmeyen. Bir uyuşmazlık varsa ortaya <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind?displayProperty=nameWithType> ancak <xref:System.TimeZoneInfo> nesnesi, yerel saat dilimini temsil etmez veya <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind?displayProperty=nameWithType> ancak <xref:System.TimeZoneInfo> nesne eşit değil <xref:System.DateTimeKind?displayProperty=nameWithType>.

Bu yöntemlerin ele <xref:System.DateTime> parametreler ve dönüş değerleri bir <xref:System.DateTime> değeri. İçin <xref:System.DateTimeOffset> değerleri, <xref:System.DateTimeOffset> yapısının bir <xref:System.DateTimeOffset.ToUniversalTime%2A> örnek tarih ve saati geçerli örneğinin UTC'ye dönüştürür yöntemi. Aşağıdaki örnek çağrıları <xref:System.DateTimeOffset.ToUniversalTime%2A> yerel saat ile birkaç kez Eşgüdümlü Evrensel Saat (UTC) dönüştürmek için yöntem.

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Belirtilen bir saat dilimi UTC Dönüştürme

UTC yerel saate dönüştürme için aşağıdaki "yerel için UTC saat dönüştürme" bölümüne bakın. UTC saat belirttiğiniz herhangi bir saat dilimi, dönüştürmek için arama <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> yöntemi. Yöntemi iki parametre alır:

* Dönüştürülecek UTC. Bu bir <xref:System.DateTime> özelliği değeri <xref:System.DateTime.Kind%2A> özelliği ayarlanmış `Unspecified` veya `Utc`.

* UTC'ye dönüştürmek için saat dilimi.

Aşağıdaki kodu Orta Standart Saati UTC dönüştürür.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>UTC yerel saate dönüştürme

Yerel saat olarak UTC dönüştürmek için çağrı <xref:System.DateTime.ToLocalTime%2A> yöntemi <xref:System.DateTime> zamanı dönüştürmek istediğiniz nesne. Yöntemi, tam davranışını nesnenin değerine bağlıdır <xref:System.DateTime.Kind%2A> özelliği, aşağıdaki tabloda gösterildiği gibi.

| `DateTime.Kind`            | Dönüştürme                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Döndürür <xref:System.DateTime> değişmeden değeri.                                      |
| `DateTimeKind.Unspecified` | Varsayar <xref:System.DateTime> değer UTC ve yerel zamana UTC dönüştürür. |
| `DateTimeKind.Utc`         | Dönüştürür <xref:System.DateTime> yerel saat değeri.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Yöntemi için aynı şekilde davranır `DateTime.ToLocalTime` yöntemi. Tek bir parametre dönüştürmek için tarih ve saat değeri olduğu alır.

Kullanarak yerel saate hiçbir atanan saat dilimi zamanında dönüştürebilirsiniz `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, sonraki bölümde ele alınmıştır.

## <a name="converting-between-any-two-time-zones"></a>Her iki saat dilimleri arasında dönüştürme

Aşağıdaki iki birini kullanarak herhangi iki saat dilimleri arasında dönüştürme `static` (`Shared` Visual Basic'te) yöntemlerinin <xref:System.TimeZoneInfo> sınıfı:

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  Bu yöntemin parametreleri dönüştürmek için tarih ve saat değeri olan bir `TimeZoneInfo` tarih ve saat değeri saat dilimini temsil eden nesnesi ve `TimeZoneInfo` tarih ve saat değerine dönüştürmek için saat dilimini temsil eden nesne.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Bu yöntemin tarih ve saat değerine dönüştürmek için tarih ve saat değerinin saat dilimi tanıtıcısı ve saat dilimi tanımlayıcı tarih ve saat değerine dönüştürmek için parametreleridir.

Her iki yöntem gerektiren <xref:System.DateTime.Kind%2A> dönüştürmek için tarih ve saat değeri özelliğine ve <xref:System.TimeZoneInfo> saat dilimini temsil eden nesne ya da saat dilimi tanımlayıcı bir başkasına karşılık gelir. Aksi halde, bir <xref:System.ArgumentException> oluşturulur. Örneğin, varsa `Kind` tarih ve saat değeri özelliği `DateTimeKind.Local`, varsa bir özel durum `TimeZoneInfo` yönteme parametre olarak geçirilen nesne eşit değil `TimeZoneInfo.Local`. Yönteme parametre olarak geçirilen tanımlayıcı eşit değilse, bir özel ayrıca durum `TimeZoneInfo.Local.Id`.

Aşağıdaki örnek kullanır <xref:System.TimeZoneInfo.ConvertTime%2A> Hawaii Standart Saati yerel saate dönüştürmek için yöntem.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>DateTimeOffset değerlerinin dönüştürme

Tarafından temsil edilen tarih ve saat değerleri <xref:System.DateTimeOffset> nesneleri tam olarak saat dilimi olmayan nesne saati kendi saat diliminden ilişkilendirmesi olduğundan kullanan bu örneği. Ancak, çoğu durumda uygulama yalnızca bir tarihi dönüştürmek gereken ve zamanı UTC gelen iki farklı uzaklıkları yerine zaman özellikle saat dilimleri tabanlı. Bu dönüştürme gerçekleştirmek için geçerli örneğin çağırabilirsiniz <xref:System.DateTimeOffset.ToOffset%2A> yöntemi. Yöntemin tek bir parametre yöntemi getirmektir saat değeri ve yeni tarihi uzaklığı.

Örneğin, bir kullanıcının saat ve tarihi için isterse bir Web sayfası bilinir ve aa/gg/yyyy ss: dd: zzzz, aşağıdaki biçiminde bir dize olarak serileştirilmiş `ReturnTimeOnServer` yöntemi tarih ve saat Web sunucusunda bu tarih ve saat değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Dize yöntemi aktarılırsa "1/9/2007 5:32:07-05: 00" temsil eden tarih ve saati bir saat diliminde UTC'den önceki beş saat, 1/9/2007 döndürür 3:32:07 AM-07: 00 ABD'de bulunan bir sunucu için Pasifik Standart saat dilimi.

<xref:System.TimeZoneInfo> Sınıfı ayrıca bir aşırı yüklemesini içerir <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> saat dilimi dönüşümleri gerçekleştirir yöntemi <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> değerleri. Yöntemin parametreleri bir <xref:System.DateTimeOffset> değer ve zaman olduğu dönüştürülecek saat dilimi başvuru. Yöntem çağrısının döndüren bir <xref:System.DateTimeOffset> değeri. Örneğin, `ReturnTimeOnServer` yöntemi önceki örnekte yeniden yazılmıştır gibi çağırmak için <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> yöntemi.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.TimeZoneInfo>[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
