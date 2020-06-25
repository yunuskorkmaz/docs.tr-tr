---
title: DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo karşılaştırması
description: .NET 'teki tarih ve saat bilgilerini temsil etmek için DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo türleri arasındaki farklılıklar hakkında bilgi edinin.
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
ms.openlocfilehash: 03d00fb802032b981a5ebe80f7166eba0fb54a60
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326047"
---
# <a name="choose-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapın

.NET uygulamaları, tarih ve saat bilgilerini çeşitli yollarla kullanabilir. Tarih ve saat bilgilerinin daha yaygın kullanımları şunlardır:

- Yalnızca bir tarihi yansıtmak için zaman bilgileri önemli değildir.

- Yalnızca bir zamanı yansıtmak için tarih bilgileri önemli değildir.

- Belirli bir zamana ve yere bağlı olmayan bir soyut tarih ve saati yansıtmak için (örneğin, çoğu gün 9:00 ' de gece yarısı açık olan uluslararası bir zincirde depolar).

- .NET dışındaki kaynaklardan tarih ve saat bilgilerini almak için genellikle tarih ve saat bilgilerinin basit bir veri türünde depolandığı yerdir.

- Tek bir zaman noktasını benzersiz ve kesin bir şekilde tanımlamak için. Bazı uygulamalar, bir tarih ve saatin yalnızca konak sisteminde olmasını gerektirir. Diğer uygulamalar, sistemler arasında (bir sistemde serileştirilmiş bir tarih, anlamlı olarak seri durumdan çıkarılmış ve dünyanın herhangi bir yerindeki başka bir sistemde kullanılabilir) olmasını gerektirir.

- Birden çok ilgili zamanı korumak için (istek sahibinin yerel saati ve sunucunun bir Web isteği için alındığını alma zamanı).

- Zaman içinde tek bir noktayı benzersiz ve kesin bir şekilde tanımlayan bir sonuçla birlikte tarih ve saat aritmetiği gerçekleştirmek için.

.Net <xref:System.DateTime> , <xref:System.DateTimeOffset> <xref:System.TimeSpan> <xref:System.TimeZoneInfo> tarihler ve saatler ile çalışan uygulamalar oluşturmak için kullanılabilen,, ve türlerini içerir.

> [!NOTE]
> Bu konu, <xref:System.TimeZone> işlevselliği sınıfında neredeyse tamamen dahil olduğu için anlatılmamaktadır <xref:System.TimeZoneInfo> . Mümkün olduğunda sınıfı <xref:System.TimeZoneInfo> yerine sınıfını kullanın <xref:System.TimeZone> .

## <a name="the-datetime-structure"></a>DateTime yapısı

Bir <xref:System.DateTime> değer belirli bir tarih ve saati tanımlar. <xref:System.DateTime.Kind%2A>Bu, tarih ve saatin ait olduğu saat dilimiyle ilgili sınırlı bilgiler sağlayan bir özelliği içerir. <xref:System.DateTimeKind>Özelliği tarafından döndürülen değer, <xref:System.DateTime.Kind%2A> <xref:System.DateTime> değerin yerel saati ( <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ), Eşgüdümlü Evrensel Saat (UTC) ( <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ) veya belirtilmeyen bir süreyi () temsil ettiğini gösterir <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> .

<xref:System.DateTime>Yapı, aşağıdaki özelliklerden birini veya daha fazlasını içeren uygulamalar için uygundur:

- Yalnızca tarihlerle çalışın.

- Yalnızca sürelerle çalışın.

- Soyut tarihler ve saatler ile çalışın.

- Saat dilimi bilgilerinin eksik olduğu tarih ve saatlerle çalışın.

- Yalnızca UTC Tarih ve saatleriyle çalışın.

- SQL veritabanları gibi .NET dışındaki kaynaklardan tarih ve saat bilgilerini alın. Genellikle, bu kaynaklar tarih ve saat bilgilerini yapısıyla uyumlu basit bir biçimde depolar <xref:System.DateTime> .

- Tarih ve saat aritmetiği yapın, ancak genel sonuçlarla ilgilenin. Örneğin, belirli bir tarih ve saate altı ay ekleyen bir toplama işleminde, sonucun gün ışığından yararlanma saatine göre ayarlanmasının gerekip gerekmediğini genellikle önemli değildir.

Belirli bir <xref:System.DateTime> değer UTC 'yi temsil etmediği takdirde, bu tarih ve saat değeri genellikle bunun taşınabilirliği içinde belirsizdir veya sınırlıdır. Örneğin, bir <xref:System.DateTime> değer yerel saati gösteriyorsa, bu yerel saat dilimi içinde taşınabilir (yani değer aynı saat diliminde başka bir sistemde seri durumdan çıkarılacağından, bu değer hala kesin bir şekilde tek bir noktayı tanımlar). Yerel saat diliminin dışında, bu <xref:System.DateTime> değerde birden çok yorumlamalar olabilir. Değerin <xref:System.DateTime.Kind%2A> özelliği ise <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , daha az taşınabilir: artık aynı saat dilimi içinde ve muhtemelen ilk serileştirildiği sisteme bile belirsizdir. Yalnızca bir <xref:System.DateTime> değer UTC 'yi gösteriyorsa, bu değerin değerin kullanıldığı sistem veya saat diliminden bağımsız olarak tek bir zaman noktasını kesin bir şekilde tanımlaması durumunda.

> [!IMPORTANT]
> Verileri kaydetme veya paylaşma sırasında <xref:System.DateTime> UTC kullanılmalıdır ve <xref:System.DateTime> değerin <xref:System.DateTime.Kind%2A> özelliği olarak ayarlanmalıdır <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset yapısı

<xref:System.DateTimeOffset>Yapı, bir tarih ve saat değerini temsil eder ve bu DEĞERIN UTC 'den ne kadar farklı olduğunu gösteren bir uzaklığa sahip. Bu nedenle, değer her zaman kesin olarak tek bir noktayı tanımlar.

<xref:System.DateTimeOffset>Türü, <xref:System.DateTime> saat dilimi tanıma ile birlikte türün tüm işlevlerini içerir. Bu, aşağıdaki uygulamalar için uygun hale getirir:

- Tek bir zaman noktasını benzersiz ve kesin bir şekilde tanımlar. <xref:System.DateTimeOffset>Türü, "Şimdi" anlamını, işlem sürelerini günlüğe kaydetmek, sistem veya uygulama olaylarının saatlerini günlüğe kaydetmek ve dosya oluşturma ve değiştirme zamanlarını kaydetmek için kullanılabilir.

- Genel Tarih ve saat aritmetiği gerçekleştirin.

- Bu süreler iki ayrı değer olarak veya bir yapının iki üyesi olarak depolandığı sürece birden çok ilgili zamanı koruyun.

> [!NOTE]
> Değerler için bu kullanımlar <xref:System.DateTimeOffset> , değerlerden çok daha yaygındır <xref:System.DateTime> . Sonuç olarak, <xref:System.DateTimeOffset> uygulama geliştirme için varsayılan tarih ve saat türünü göz önünde bulundurun.

Bir <xref:System.DateTimeOffset> değer belirli bir saat dilimine bağlı değildir, ancak çeşitli saat dilimlerden kaynaklanalabilir. Aşağıdaki örnekte, bir dizi <xref:System.DateTimeOffset> değerin (yerel Pasifik standart saati dahil) ait olduğu saat dilimleri listelenmektedir.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Çıktı, bu örnekteki her bir tarih ve saat değerinin en az üç farklı saat dilimine ait olduğunu gösterir. <xref:System.DateTimeOffset>6/10/2007 değeri, bir tarih ve saat değeri gün ışığından yararlanma süresini gösteriyorsa, UTC arasındaki fark, kaynak saat diliminin temel UTC denkleye karşılık gelir veya görünen ADıNDA UTC 'den gelen uzaklığa karşılık gelmelidir. Tek bir <xref:System.DateTimeOffset> değer, saat dilimiyle sıkı bir şekilde bağlı olmadığından, gün ışığından yararlanma saatine kadar bir saat diliminin geçişini yansıtmaz. Bu, bir değeri işlemek için tarih ve saat aritmetiği kullanıldığında soruna neden olabilir <xref:System.DateTimeOffset> . Tarih ve saat aritmetiğini bir saat diliminin ayarlama kurallarının hesabını alan bir şekilde gerçekleştirme hakkında bir tartışma için bkz. [Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>TimeSpan yapısı

<xref:System.TimeSpan>Yapı bir zaman aralığını temsil eder. Bu iki genel kullanım şunlardır:

- İki tarih ve saat değeri arasındaki zaman aralığını yansıtır. Örneğin, bir değeri başka bir değerden çıkarmak bir <xref:System.DateTime> <xref:System.TimeSpan> değer döndürür.

- Geçen süreyi ölçme. Örneğin, özelliği, <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> <xref:System.TimeSpan> <xref:System.Diagnostics.Stopwatch> geçen süreyi ölçmeye başlayan metotlardan birine yapılan çağrıdan bu yana geçen zaman aralığını yansıtan bir değer döndürür.

Değer <xref:System.TimeSpan> , <xref:System.DateTime> belirli bir güne başvuru olmadan bir saati yansıttığına bir değer değişikliği olarak da kullanılabilir. Bu kullanım, <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> <xref:System.TimeSpan> bir tarih başvurusu olmadan saati temsil eden bir değer döndüren ve özelliklerine benzerdir. Örneğin, yapı, <xref:System.TimeSpan> deponun günlük açma veya kapatma süresini yansıtmak için veya herhangi bir normal olayın gerçekleştiği süreyi temsil etmek için kullanılabilir.

Aşağıdaki örnek, deponun `StoreInfo` <xref:System.TimeSpan> <xref:System.TimeZoneInfo> saat dilimini temsil eden bir nesnenin yanı sıra, mağaza açma ve kapatma süreleri için nesneleri içeren bir yapıyı tanımlar. Yapı ayrıca iki yöntem içerir `IsOpenNow` ve bu, `IsOpenAt` deponun Kullanıcı tarafından belirtilen bir anda açık olup olmadığını, yerel saat diliminde olduğunu varsaydığını gösterir.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo`Yapı daha sonra aşağıdaki gibi istemci kodu tarafından kullanılabilir.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo sınıfı

<xref:System.TimeZoneInfo>Sınıfı, dünya zamanının herhangi birini temsil eder ve bir saat dilimindeki tarih ve saatin başka bir saat dilimiyle eşdeğer olarak dönüştürülmesini sağlar. <xref:System.TimeZoneInfo>Sınıf, tarih ve saatlerle çalışmayı mümkün kılar, böylece herhangi bir tarih ve saat değeri belirsiz bir zamanda tek bir noktayı tanımlar. <xref:System.TimeZoneInfo>Sınıfı da genişletilebilir. Windows sistemleri için sunulan ve kayıt defterinde tanımlanan saat dilimi bilgilerine bağlı olsa da, özel saat dilimlerini oluşturmayı destekler. Ayrıca, saat dilimi bilgilerinin serileştirilmesi ve serisini kaldırma işlemi de desteklenir.

Bazı durumlarda, sınıfın tüm avantajlarından yararlanmak için <xref:System.TimeZoneInfo> daha fazla geliştirme çalışması gerekebilir. Tarih ve saat değerleri, ait oldukları Saat dilimleriyle sıkı bir şekilde bağlı değilse, daha fazla çalışma gerekir. Uygulamanız bir tarih ve saati ilişkili saat dilimiyle bağlamak için bazı mekanizmalar sunmadığı takdirde, belirli bir tarih ve saat değerinin saat diliminden bir ilişkisi olması kolaylaşır. Bu bilgileri bağlamak için bir yöntem, hem tarih hem de saat değeri ile ilişkili saat dilimi nesnesini içeren bir sınıf veya yapı tanımlamaktır.

.NET 'teki saat dilimi desteğinden yararlanmak için, tarih ve saat değerinin oluşturulduğu zaman dilimini bilmeniz gerekir. Saat dilimi genellikle Web veya ağ uygulamalarında bilinen değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
