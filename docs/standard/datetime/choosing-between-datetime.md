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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c4eb8c174e70b6761784a5defe12dc8a8a1e42b
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107075"
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

.Net <xref:System.DateTime> <xref:System.DateTimeOffset> ,tarihler<xref:System.TimeZoneInfo> ve saatler ile çalışan uygulamalar oluşturmak için kullanılabilen, ,vetürleriniiçerir.<xref:System.TimeSpan>

> [!NOTE]
> Bu konu, işlevselliği <xref:System.TimeZone> <xref:System.TimeZoneInfo> sınıfında neredeyse tamamen dahil olduğu için anlatılmamaktadır. Mümkün olduğunda sınıfı yerine <xref:System.TimeZoneInfo> <xref:System.TimeZone> sınıfını kullanın.

## <a name="the-datetime-structure"></a>DateTime yapısı

Bir <xref:System.DateTime> değer belirli bir tarih ve saati tanımlar. Bu, Tarih <xref:System.DateTime.Kind%2A> ve saatin ait olduğu saat dilimiyle ilgili sınırlı bilgiler sağlayan bir özelliği içerir. <xref:System.DateTimeKind.Utc?displayProperty=nameWithType><xref:System.DateTimeKind.Local?displayProperty=nameWithType><xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>Özelliği tarafından döndürülen <xref:System.DateTime> değer, değerin yerel saati (), Eşgüdümlü Evrensel Saat (UTC) () veya belirtilmeyen bir süreyi () temsil ettiğini gösterir. <xref:System.DateTimeKind> <xref:System.DateTime.Kind%2A>

<xref:System.DateTime> Yapı, aşağıdakileri gerçekleştiren uygulamalar için uygundur:

- Yalnızca tarihlerle çalışın.

- Yalnızca sürelerle çalışın.

- Soyut tarihler ve saatler ile çalışın.

- Saat dilimi bilgilerinin eksik olduğu tarih ve saatlerle çalışın.

- Yalnızca UTC Tarih ve saatleriyle çalışın.

- SQL veritabanları gibi .NET dışındaki kaynaklardan tarih ve saat bilgilerini alın. Genellikle, bu kaynaklar tarih ve saat bilgilerini <xref:System.DateTime> yapısıyla uyumlu basit bir biçimde depolar.

- Tarih ve saat aritmetiği yapın, ancak genel sonuçlarla ilgilenin. Örneğin, belirli bir tarih ve saate altı ay ekleyen bir toplama işleminde, sonucun gün ışığından yararlanma saatine göre ayarlanmasının gerekip gerekmediğini genellikle önemli değildir.

Belirli <xref:System.DateTime> bir değer UTC 'yi temsil etmediği takdirde, bu tarih ve saat değeri genellikle bunun taşınabilirliği içinde belirsizdir veya sınırlıdır. Örneğin, bir <xref:System.DateTime> değer yerel saati gösteriyorsa, bu yerel saat dilimi içinde taşınabilir (yani değer aynı saat diliminde başka bir sistemde seri durumdan çıkarılacağından, bu değer hala kesin bir şekilde tek bir noktayı tanımlar). Yerel saat diliminin dışında, bu <xref:System.DateTime> değerde birden çok yorumlamalar olabilir. Değerin <xref:System.DateTime.Kind%2A> özelliği ise <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, daha az taşınabilir: artık aynı saat dilimi içinde ve muhtemelen ilk serileştirildiği sisteme bile belirsizdir. Yalnızca bir <xref:System.DateTime> değer UTC 'yi gösteriyorsa, bu değerin değerin kullanıldığı sistem veya saat diliminden bağımsız olarak tek bir zaman noktasını kesin bir şekilde tanımlaması durumunda.

> [!IMPORTANT]
> Verileri kaydetme veya paylaşma <xref:System.DateTime> sırasında UTC kullanılmalıdır <xref:System.DateTime> ve değerin <xref:System.DateTime.Kind%2A> özelliği olarak <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>ayarlanmalıdır.

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset yapısı

<xref:System.DateTimeOffset> Yapı, bir tarih ve saat değerini temsil eder ve bu değerin UTC 'den ne kadar farklı olduğunu gösteren bir uzaklığa sahip. Bu nedenle, değer her zaman kesin olarak tek bir noktayı tanımlar.

Türü, saat dilimi tanıma ile birlikte <xref:System.DateTime> türün tüm işlevlerini içerir. <xref:System.DateTimeOffset> Bu, aşağıdakileri gerçekleştiren uygulamalar için uygun hale getirir:

- Tek bir zaman noktasını benzersiz ve kesin bir şekilde tanımlar. <xref:System.DateTimeOffset> Türü, "Şimdi" anlamını, işlem sürelerini günlüğe kaydetmek, sistem veya uygulama olaylarının saatlerini günlüğe kaydetmek ve dosya oluşturma ve değiştirme zamanlarını kaydetmek için kullanılabilir.

- Genel Tarih ve saat aritmetiği gerçekleştirin.

- Bu süreler iki ayrı değer olarak veya bir yapının iki üyesi olarak depolandığı sürece birden çok ilgili zamanı koruyun.

> [!NOTE]
> Değerler için <xref:System.DateTimeOffset> bu kullanımlar, <xref:System.DateTime> değerlerden çok daha yaygındır. Sonuç olarak, <xref:System.DateTimeOffset> uygulama geliştirme için varsayılan tarih ve saat türü olarak düşünülmelidir.

Bir <xref:System.DateTimeOffset> değer belirli bir saat dilimine bağlı değildir, ancak çeşitli saat dilimlerden kaynaklanmayabilir. Bunu göstermek için aşağıdaki örnekte, bir dizi <xref:System.DateTimeOffset> değerin (bir yerel Pasifik standart saati dahil) ait olduğu saat dilimleri listelenmektedir.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Çıktı, bu örnekteki her bir tarih ve saat değerinin en az üç farklı saat dilimine ait olduğunu gösterir. 6/10/2007 <xref:System.DateTimeOffset> değeri, bir tarih ve saat değeri gün ışığından yararlanma süresini gösteriyorsa, UTC 'nin değerinin, kaynak saat diliminin temel UTC denkleyede veya görünen adında UTC 'den gelen uzaklığa karşılık gelmesi gerektiğini gösterir. Yani tek <xref:System.DateTimeOffset> bir değer, saat dilimiyle sıkı bir şekilde bağlı olmadığından, zaman diliminin günışığından yararlanma saatine kadar bir saat dilimine geçişini yansıtamaz. Bu, bir <xref:System.DateTimeOffset> değeri işlemek için tarih ve saat aritmetiği kullanıldığında özellikle soruna neden olabilir. (Tarih ve saat aritmetiği bir saat diliminin ayarlama kurallarının hesabını alan bir şekilde gerçekleştirme hakkında bir tartışma için bkz. [Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>TimeSpan yapısı

<xref:System.TimeSpan> Yapı bir zaman aralığını temsil eder. Bu iki genel kullanım şunlardır:

- İki tarih ve saat değeri arasındaki zaman aralığını yansıtır. Örneğin, bir <xref:System.DateTime> değeri başka bir değerden çıkarmak bir <xref:System.TimeSpan> değer döndürür.

- Geçen süreyi ölçme. Örneğin, <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> özelliği, geçen süreyi ölçmeye başlayan <xref:System.Diagnostics.Stopwatch> metotlardan birine yapılan çağrıdan bu yana geçen zaman aralığını yansıtan bir <xref:System.TimeSpan> değer döndürür.

Değer, belirli bir güne başvuru olmadan bir saati yansıttığına bir <xref:System.DateTime> değer değişikliği olarak da kullanılabilir. <xref:System.TimeSpan> Bu kullanım, bir tarih başvurusu <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> olmadan <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> saati temsil eden bir <xref:System.TimeSpan> değer döndüren ve özelliklerine benzerdir. Örneğin, <xref:System.TimeSpan> yapı, deponun günlük açma veya kapatma süresini yansıtmak için veya herhangi bir normal olayın gerçekleştiği süreyi temsil etmek için kullanılabilir.

Aşağıdaki örnek, deponun saat `StoreInfo` dilimini temsil eden <xref:System.TimeSpan> bir <xref:System.TimeZoneInfo> nesnenin yanı sıra, mağaza açma ve kapatma süreleri için nesneleri içeren bir yapıyı tanımlar. Yapı ayrıca iki yöntem `IsOpenNow` içerir ve `IsOpenAt`bu, deponun Kullanıcı tarafından belirtilen bir anda açık olup olmadığını, yerel saat diliminde olduğunu varsaydığını gösterir.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Yapı daha sonra aşağıdaki gibi istemci kodu tarafından kullanılabilir.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo sınıfı

<xref:System.TimeZoneInfo> Sınıfı, dünya zamanının herhangi birini temsil eder ve bir saat dilimindeki tarih ve saatin başka bir saat dilimiyle eşdeğer olarak dönüştürülmesini sağlar. Sınıf <xref:System.TimeZoneInfo> , tarih ve saatlerle çalışmayı mümkün kılar, böylece herhangi bir tarih ve saat değeri belirsiz bir zamanda tek bir noktayı tanımlar. <xref:System.TimeZoneInfo> Sınıfı da genişletilebilir. Windows sistemleri için sunulan ve kayıt defterinde tanımlanan saat dilimi bilgilerine bağlı olsa da, özel saat dilimlerini oluşturmayı destekler. Ayrıca, saat dilimi bilgilerinin serileştirilmesi ve serisini kaldırma işlemi de desteklenir.

Bazı durumlarda, sınıfın tüm avantajlarından yararlanmak için <xref:System.TimeZoneInfo> daha fazla geliştirme çalışması gerekebilir. Tarih ve saat değerleri, ait oldukları Saat dilimleriyle sıkı bir şekilde bağlı değilse, daha fazla çalışma gerekir. Uygulamanız bir tarih ve saati ilişkili saat dilimiyle bağlamak için bazı mekanizmalar sunmadığı takdirde, belirli bir tarih ve saat değerinin saat diliminden bir ilişkisi olması kolaylaşır. Bu bilgileri bağlamak için bir yöntem, hem tarih hem de saat değeri ile ilişkili saat dilimi nesnesini içeren bir sınıf veya yapı tanımlamaktır.

.NET 'teki saat dilimi desteğinin avantajlarından yararlanmak, yalnızca tarih ve saat değerinin ait olduğu saat dilimi söz konusu tarih ve saat nesnesi örneği oluşturulduğunda bilindiğinde mümkündür. Özellikle Web veya ağ uygulamalarında bu durum genellikle değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
