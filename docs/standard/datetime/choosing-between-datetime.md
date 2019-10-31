---
title: DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
ms.openlocfilehash: 5425d94daf8ab023bef4a1a68f06d5c276499825
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132571"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma

Tarih ve saat bilgilerini kullanan .NET uygulamaları çok farklı ve bu bilgileri çeşitli yollarla kullanabilir. Tarih ve saat bilgilerinin daha yaygın kullanımları, aşağıdakilerden birini veya daha fazlasını içerir:

- Yalnızca bir tarihi yansıtmak için zaman bilgileri önemli değildir.

- Yalnızca bir zamanı yansıtmak için tarih bilgileri önemli değildir.

- Belirli bir zamana ve yere bağlı olmayan bir soyut tarih ve saati yansıtmak için (örneğin, çoğu gün 9:00 ' de gece yarısı açık olan uluslararası bir zincirde depolar).

- .NET dışındaki kaynaklardan tarih ve saat bilgilerini almak için genellikle tarih ve saat bilgilerinin basit bir veri türünde depolandığı yerdir.

- Tek bir zaman noktasını benzersiz ve kesin bir şekilde tanımlamak için. Bazı uygulamalar, bir tarih ve saatin yalnızca konak sisteminde olmasını gerektirir; Diğerleri, sistemlerin genelinde (bir sistemde serileştirilmiş bir tarih, anlamlı olarak seri durumdan çıkarılmış ve dünyanın herhangi bir yerindeki başka bir sistemde kullanılan bir tarih) olmasını gerektirir.

- Birden çok ilgili zamanı korumak için (istek sahibinin yerel saati ve sunucunun bir Web isteği için alındığını alma zamanı).

- Zaman içinde tek bir noktayı benzersiz ve kesin bir şekilde tanımlayan bir sonuçla birlikte tarih ve saat aritmetiği gerçekleştirmek için.

.NET, hepsi tarih ve saatlerle çalışan uygulamalar oluşturmak için kullanılabilecek <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>ve <xref:System.TimeZoneInfo> türlerini içerir.

> [!NOTE]
> Bu konu, işlevselliği <xref:System.TimeZoneInfo> sınıfında neredeyse tamamen dahil olduğundan <xref:System.TimeZone> ele almaz. Mümkün olduğunda, <xref:System.TimeZone> sınıfı yerine <xref:System.TimeZoneInfo> sınıfını kullanın.

## <a name="the-datetime-structure"></a>DateTime yapısı

<xref:System.DateTime> değeri belirli bir tarih ve saati tanımlar. Bu, tarih ve saatin ait olduğu saat dilimiyle ilgili sınırlı bilgiler sağlayan bir <xref:System.DateTime.Kind%2A> özelliği içerir. <xref:System.DateTime.Kind%2A> özelliği tarafından döndürülen <xref:System.DateTimeKind> değeri, <xref:System.DateTime> değerin yerel saati (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Eşgüdümlü Evrensel Saat (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) veya belirtilmeyen bir süreyi (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>) temsil ettiğini belirtir.

<xref:System.DateTime> yapısı aşağıdakileri gerçekleştiren uygulamalar için uygundur:

- Yalnızca tarihlerle çalışın.

- Yalnızca sürelerle çalışın.

- Soyut tarihler ve saatler ile çalışın.

- Saat dilimi bilgilerinin eksik olduğu tarih ve saatlerle çalışın.

- Yalnızca UTC Tarih ve saatleriyle çalışın.

- SQL veritabanları gibi .NET dışındaki kaynaklardan tarih ve saat bilgilerini alın. Genellikle, bu kaynaklar tarih ve saat bilgilerini <xref:System.DateTime> yapısıyla uyumlu basit bir biçimde depolar.

- Tarih ve saat aritmetiği yapın, ancak genel sonuçlarla ilgilenin. Örneğin, belirli bir tarih ve saate altı ay ekleyen bir toplama işleminde, sonucun gün ışığından yararlanma saatine göre ayarlanmasının gerekip gerekmediğini genellikle önemli değildir.

Belirli bir <xref:System.DateTime> değeri UTC 'yi temsil etmediği takdirde, bu tarih ve saat değeri genellikle taşınabilirliği içinde belirsizdir veya sınırlıdır. Örneğin, bir <xref:System.DateTime> değeri yerel saati gösteriyorsa, bu yerel saat dilimi içinde taşınabilir (yani değer aynı saat diliminde başka bir sistemde seri durumdan çıkarılacağından, bu değer hala kesin bir zamanda tek bir noktayı tanımlar). Yerel saat diliminin dışında, bu <xref:System.DateTime> değer birden çok yorumlamalar içerebilir. Değerin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, daha az taşınabilir: artık aynı saat dilimi içinde ve muhtemelen ilk serileştirildiği sisteme bile belirsizdir. Yalnızca bir <xref:System.DateTime> değeri UTC 'yi gösteriyorsa, bu değerin değerin kullanıldığı sistem veya saat diliminden bağımsız olarak tek bir zaman noktasını kesin bir şekilde tanımlaması durumunda.

> [!IMPORTANT]
> <xref:System.DateTime> verileri kaydederken veya paylaşarak UTC kullanılmalıdır ve <xref:System.DateTime> değerin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>olarak ayarlanmalıdır.

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset yapısı

<xref:System.DateTimeOffset> yapısı bir tarih ve saat değerini, bu değerin UTC 'den ne kadar farklılık gösterdiğini gösteren bir uzaklığa göre temsil eder. Bu nedenle, değer her zaman kesin olarak tek bir noktayı tanımlar.

<xref:System.DateTimeOffset> türü, saat dilimi tanıma ile birlikte <xref:System.DateTime> türünün tüm işlevlerini içerir. Bu, aşağıdakileri gerçekleştiren uygulamalar için uygun hale getirir:

- Tek bir zaman noktasını benzersiz ve kesin bir şekilde tanımlar. <xref:System.DateTimeOffset> türü, "Şimdi" öğesinin anlamını kesin bir şekilde tanımlamak, işlem sürelerini günlüğe kaydetmek, sistem veya uygulama olaylarının saatlerini günlüğe kaydetmek ve dosya oluşturma ve değiştirme zamanlarını kaydetmek için kullanılabilir.

- Genel Tarih ve saat aritmetiği gerçekleştirin.

- Bu süreler iki ayrı değer olarak veya bir yapının iki üyesi olarak depolandığı sürece birden çok ilgili zamanı koruyun.

> [!NOTE]
> <xref:System.DateTimeOffset> değerleri için bu kullanımlar, <xref:System.DateTime> değerlerinden çok daha yaygındır. Sonuç olarak, <xref:System.DateTimeOffset> uygulama geliştirme için varsayılan tarih ve saat türü olarak düşünülmelidir.

<xref:System.DateTimeOffset> bir değer belirli bir saat dilimine bağlı değildir, ancak çeşitli saat dilimlerden kaynaklanmayabilir. Bunu göstermek için aşağıdaki örnekte, bir dizi <xref:System.DateTimeOffset> değeri (yerel Pasifik standart saati dahil) olan saat dilimleri listelenmektedir.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Çıktı, bu örnekteki her bir tarih ve saat değerinin en az üç farklı saat dilimine ait olduğunu gösterir. 6/10/2007 <xref:System.DateTimeOffset> değeri, bir tarih ve saat değeri gün ışığından yararlanma saatini temsil ediyorsa, UTC değerinin, kaynak saat diliminin temel UTC denkleye karşılık gelmesi veya görünen adında UTC 'den olan uzaklığa eşit olması gerektiğini gösterir. Yani, tek bir <xref:System.DateTimeOffset> değeri kendi saat dilimiyle sıkı bir şekilde bağlı olmadığından, gün ışığından yararlanma saatine kadar bir saat diliminin geçişini yansıtmaz. Bu, bir <xref:System.DateTimeOffset> değerini işlemek için tarih ve saat aritmetiği kullanıldığında özellikle soruna neden olabilir. Tarih ve saat aritmetiğini bir saat diliminin ayarlama kurallarının hesabını alan bir şekilde gerçekleştirme hakkında bir tartışma için bkz. [Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>TimeSpan yapısı

<xref:System.TimeSpan> yapısı bir zaman aralığını temsil eder. Bu iki genel kullanım şunlardır:

- İki tarih ve saat değeri arasındaki zaman aralığını yansıtır. Örneğin, bir <xref:System.DateTime> değerini başka bir değerden çıkarmak bir <xref:System.TimeSpan> değeri döndürür.

- Geçen süreyi ölçme. Örneğin <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> özelliği, geçen süreyi ölçmeye başlayan <xref:System.Diagnostics.Stopwatch> metotlarından birine çağrıdan sonra geçen zaman aralığını yansıtan bir <xref:System.TimeSpan> değeri döndürür.

Bir <xref:System.TimeSpan> değeri, bu değer belirli bir güne başvuru olmadan bir saati yansıttığına bir <xref:System.DateTime> değerinin yerine konacak olarak da kullanılabilir. Bu kullanım, bir tarih başvurusu olmadan saati temsil eden bir <xref:System.TimeSpan> değeri döndüren <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> özelliklerine benzerdir. Örneğin, <xref:System.TimeSpan> yapısı bir deponun günlük açma veya kapatma süresini yansıtacak şekilde veya herhangi bir normal olayın gerçekleştiği süreyi temsil etmek için kullanılabilir.

Aşağıdaki örnek, deponun saat dilimini temsil eden bir <xref:System.TimeZoneInfo> nesnesi ve depolama açma ve kapatma süreleri için <xref:System.TimeSpan> nesneleri içeren bir `StoreInfo` yapısını tanımlar. Bu yapı Ayrıca, deponun Kullanıcı tarafından belirtilen bir anda açık olup olmadığını, yerel saat diliminde olduğunu varsayan `IsOpenNow` ve `IsOpenAt`iki yöntem içerir.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` yapısı daha sonra aşağıdaki gibi istemci kodu tarafından kullanılabilir.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo sınıfı

<xref:System.TimeZoneInfo> sınıfı, herhangi bir dünya saat dilimini temsil eder ve bir saat dilimindeki tarih ve saatin başka bir saat dilimiyle eşdeğer olarak dönüştürülmesini sağlar. <xref:System.TimeZoneInfo> sınıfı tarih ve saatlerle çalışmayı mümkün kılar, böylece herhangi bir tarih ve saat değeri belirsiz bir zamanda tek bir noktayı tanımlar. <xref:System.TimeZoneInfo> sınıfı da genişletilebilir. Windows sistemleri için sunulan ve kayıt defterinde tanımlanan saat dilimi bilgilerine bağlı olsa da, özel saat dilimlerini oluşturmayı destekler. Ayrıca, saat dilimi bilgilerinin serileştirilmesi ve serisini kaldırma işlemi de desteklenir.

Bazı durumlarda <xref:System.TimeZoneInfo> sınıftan tam olarak yararlanmak daha fazla geliştirme çalışması gerektirebilir. Tarih ve saat değerleri, ait oldukları Saat dilimleriyle sıkı bir şekilde bağlı değilse, daha fazla çalışma gerekir. Uygulamanız bir tarih ve saati ilişkili saat dilimiyle bağlamak için bazı mekanizmalar sunmadığı takdirde, belirli bir tarih ve saat değerinin saat diliminden bir ilişkisi olması kolaylaşır. Bu bilgileri bağlamak için bir yöntem, hem tarih hem de saat değeri ile ilişkili saat dilimi nesnesini içeren bir sınıf veya yapı tanımlamaktır.

.NET 'teki saat dilimi desteğinin avantajlarından yararlanmak, yalnızca tarih ve saat değerinin ait olduğu saat dilimi söz konusu tarih ve saat nesnesi örneği oluşturulduğunda bilindiğinde mümkündür. Özellikle Web veya ağ uygulamalarında bu durum genellikle değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
