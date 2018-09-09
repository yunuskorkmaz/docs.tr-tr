---
title: DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim
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
ms.openlocfilehash: 54392ce12ca93d3a7979b1d0bbc78132773f88ce
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227720"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim

Tarih ve saat bilgilerini kullanan .NET uygulamaları çok farklı ve bu bilgileri, çeşitli yollarla kullanabilirsiniz. Bir veya daha fazlasını tarih ve saat bilgilerini daha yaygın kullanımları şunlardır:

* Yalnızca bir tarih saat bilgilerini önemli değildir. böylece yansıtacak şekilde.

* Yalnızca bir kez yansıtmak için bu nedenle, tarih bilgileri önemli değildir.

* Soyut bir tarih ve saat, belirli bir zaman ve yerde (örneğin, çoğu hafta içi günlerde saat 9: 00'da açık bir Uluslararası zincirindeki deposu) bağlı değildir.

* .NET dışındaki kaynaklardan tarih ve saat bilgilerini almak için genellikle basit bir tarih ve saat bilgilerini depolandığı veri türü.

* Benzersiz olarak ve belirsiz bir şekilde tek bir nokta sürede tanımlamak için. Bazı uygulamalar, bir tarih ve saat yalnızca ana bilgisayar sisteminde benzersiz olmasını gerektirir; diğerleri, sistemler arasında benzersiz olması gerekir (diğer bir deyişle, bir'seri hale getirilmiş bir tarih atayamayacağına seri durumdan ve dünyanın her yerinden başka bir sistemde kullanılan).

* Birden çok korumak için (örneğin, istek sahibinin yerel saat ve bir Web isteği giriş sunucunun saati) saatleri ilgili.

* Tarih ve saat gerçekleştirmek için aritmetik, büyük olasılıkla bir sonuç ile benzersiz olarak ve belirsiz bir şekilde tek bir nokta sürede tanımlar.

.NET içeren <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, ve <xref:System.TimeZoneInfo> türleri, tüm tarihler ve saatler ile çalışan uygulamalar oluşturmak için kullanılabilir.

> [!NOTE]
> Bu konuda, dördüncü bir tür anlatılmamaktadır <xref:System.TimeZone>, işlevselliği neredeyse tamamen eklenmiştir <xref:System.TimeZoneInfo> sınıfı. Mümkün olduğunda, geliştiricilerin kullanması gereken <xref:System.TimeZoneInfo> sınıfı yerine <xref:System.TimeZone> sınıfı.

## <a name="the-datetime-structure"></a>DateTime yapısı

A <xref:System.DateTime> belirli tarih ve saat değeri tanımlar. İçerdiği bir <xref:System.DateTime.Kind%2A> sağlayan özelliği sınırlı saat dilimine hakkında bilgi, tarih ve saat ait. <xref:System.DateTimeKind> Tarafından döndürülen değer <xref:System.DateTime.Kind%2A> özelliği belirtir olup olmadığını <xref:System.DateTime> değer yerel saat temsil eder (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Eşgüdümlü Evrensel Saat (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), veya belirtilmeyen bir saat (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

<xref:System.DateTime> Yapısı aşağıdakileri uygulamalar için uygundur:

* Yalnızca tarih ile çalışır.

* Saatler ile çalışma.

* Soyut tarihler ve saatler ile çalışma.

* Tarihler ve saatler için hangi saat dilimi bilgileri eksik çalışın.

* UTC tarih ve saatlerle yalnızca çalışır.

* SQL veritabanları gibi .NET dışındaki kaynaklardan tarih ve saat bilgilerini alır. Genellikle, bu kaynakları tarih ve saat bilgilerini ile uyumlu olan basit bir biçimde depolamak <xref:System.DateTime> yapısı.

* Tarih gerçekleştirin ve saat aritmetiğinde, ancak bunlar genel sonuçları ilgilenir. Örneğin, belirli bir tarih ve saat için altı ay ekleyen bir toplama işleminde sonuç ışığından yararlanma saatine göre mi ayarlanır önemlidir değildir.

Sürece belirli bir <xref:System.DateTime> değeri temsil UTC, o tarih ve saat değeri genellikle belirsiz veya kendi taşınabilirlik sınırlıydı. Örneğin, bir <xref:System.DateTime> değer yerel saat temsil eder (diğer bir deyişle, değer aynı saat diliminde değer sürede yine de kesin bir şekilde tek bir noktadan tanımlar, başka bir sistemde seri durumda değilse), yerel saat dilimi içinde taşınabilir. Yerel saat dilimi dışında <xref:System.DateTime> değeri, birden çok yorumlaması olabilir. Değerin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, bile daha az taşınabilir: artık aynı saat diliminde içinde ve büyük olasılıkla, onu önce seri hale getirilmiş bile aynı sistemde belirsiz olduğu. Yalnızca bir <xref:System.DateTime> değer değer üretemez tek bir nokta saat dilimi değeri kullanılır ve sistem bakılmaksızın zaman içinde tanımlamasını UTC mu temsil eder.

> [!IMPORTANT]
> Paylaşımı veya kaydederken <xref:System.DateTime> veri, UTC kullanılmalıdır ve <xref:System.DateTime> değerinin <xref:System.DateTime.Kind%2A> özelliği ayarlanmalıdır <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset yapısı

<xref:System.DateTimeOffset> Yapısı UTC'den ne kadar bu değeri farklılık gösteren bir uzaklık birlikte bir tarih ve saat değerini temsil eder. Bu nedenle, değer zamanında tek bir nokta her zaman kesin bir şekilde tanımlar.

<xref:System.DateTimeOffset> Türünü içeren tüm işlevlerini <xref:System.DateTime> saat dilimini tanıma birlikte türü. Bu aşağıdakileri gerçekleştiren uygulamalar için uygun hale getirir:

* Benzersiz olarak ve belirsiz bir şekilde tek bir nokta sürede belirleyin. <xref:System.DateTimeOffset> Türü, sistem veya uygulama olayları sürelerinin oturum için "Şimdi", günlük işlem süreleri ve kayıt dosyası oluşturma ve değişiklik saatlerini anlamını kesin bir şekilde tanımlamak için kullanılabilir.

* Genel tarih ve saat aritmetiğini gerçekleştirme.

* Birden çok koruma ilgili zaman, bu kez iki ayrı değer veya bir yapının iki üyesi olarak depolanan sürece.

> [!NOTE]
> Bu kullanımları <xref:System.DateTimeOffset> değerler için olandan çok daha yaygın <xref:System.DateTime> değerleri. Sonuç olarak, <xref:System.DateTimeOffset> uygulama geliştirme için varsayılan tarih ve saat türü düşünülmelidir.

A <xref:System.DateTimeOffset> değeri belirli bir saat dilimine bağlı değildir, ancak herhangi bir saat dilimlerini çeşitli gönderilebilir. Aşağıdaki örnek bunu göstermek için hangi saat dilimlerini listeler bir dizi <xref:System.DateTimeOffset> (bir yerel Pasifik Standart Saati dahil olmak üzere) değerlerine ait.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Çıkış gösteren her bir tarih ve saat değeri bu örnekte, en az üç farklı saat dilimlerinde ait olabilir. <xref:System.DateTimeOffset> 6/10/2007 değerini gösteren bir yaz saati bir tarih ve saat değerini temsil ediyorsa, UTC uzaklığı bile mutlaka kaynak saat diliminin temel UTC farkı veya görünen adını bulunan utc'den uzaklık karşılık. Bu, çünkü anlamına tek bir <xref:System.DateTimeOffset> değeri değil sıkı şekilde bağlı kendi saat dilimiyle, için ve gün ışığından yararlanma saat diliminin geçiş yansıtacak olamaz. Tarih ve saat aritmetiği kullanıldığında işlemek için bu özellikle sorunlu olabilir bir <xref:System.DateTimeOffset> değeri. (Tarih ve saat aritmetiği saat diliminin ayarlama kuralları hesaba katar bir şekilde gerçekleştirmek nasıl bir tartışma için bkz [tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>TimeSpan yapısı

<xref:System.TimeSpan> Yapısı bir zaman aralığını temsil eder. İki tipik kullanımları şunlardır:

* İki tarih ve saat değeri arasındaki zaman aralığını yansıtan. Örneğin, bir çıkarma <xref:System.DateTime> döndürür başka bir değerden bir <xref:System.TimeSpan> değeri.

* Ölçüm geçen süre. Örneğin, <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.TimeSpan> birini çağrısından itibaren geçen zaman aralığını gösteren bir değer <xref:System.Diagnostics.Stopwatch> geçen süreyi ölçmek için başlayan yöntemleri.

A <xref:System.TimeSpan> değeri de kullanılabilir bir ardılı olarak bir <xref:System.DateTime> değeri o değerin birer günün belirli bir zamanda başvuru olmadan yansıttığında. Bu kullanım benzer <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> döndürülen özellikler, bir <xref:System.TimeSpan> olmadan bir tarihe başvuru saati gösteren bir değer. Örneğin, <xref:System.TimeSpan> yapısı, bir mağazanın günlük açılış veya kapanış saati yansıtmak için kullanılabilir veya normal herhangi bir olayın gerçekleştiği zaman temsil etmek için kullanılabilir.

Aşağıdaki örnekte tanımlayan bir `StoreInfo` içeren yapı <xref:System.TimeSpan> açılış ve kapanış süreleri, nesneleri depolamak yanı sıra bir <xref:System.TimeZoneInfo> mağazanın saat dilimini temsil eden nesne. Yapısı iki yöntem de içerir. `IsOpenNow` ve `IsOpenAt`, deponun yerel saat diliminizde varsayılır, kullanıcı tarafından belirtilen bir zamanda açık olup olmadığını gösterir.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Yapısı aşağıdaki gibi istemci kodu tarafından kullanılabilecek.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>Timezoneınfo sınıfı

<xref:System.TimeZoneInfo> Sınıfı dünya saat dilimlerini birini temsil eder ve herhangi bir tarih ve saat dilimindeki karşılığını başka bir saat dilimindeki dönüştürme sağlar. <xref:System.TimeZoneInfo> Sınıfı ile tarihleri mümkün kılan ve herhangi bir tarih ve saat değeri tek bir nokta zaman içinde kesin bir şekilde tanımlar. böylece zaman. <xref:System.TimeZoneInfo> Sınıftır da genişletilebilir. Windows sistemleri için sağlanan ve kayıt defterinde tanımlanmış saat dilimi bilgileri bağlı olsa da, özel saat dilimi oluşturulmasını destekler. Ayrıca, serileştirme ve seri durumundan çıkarma saat dilimi bilgilerinin de destekler.

Bazı durumlarda, tam yararlanarak <xref:System.TimeZoneInfo> sınıfı, daha fazla geliştirme çalışma gerektirebilir. Tarih ve saat değerlerini sıkı bir şekilde zaman, bunlar ait, daha fazla iş bölgeler ile bağlı değil değilse gereklidir. Bir tarih ve saat, ilişkili bir saat dilimi ile bağlama bazı mekanizması uygulamanızın sağladığı sürece, belirli bir tarih ve saat değerini kendi saat diliminden ilişkilendirmesi haline için kolay bir işlemdir. Bu bilgiler bağlama bir yöntemi, bir sınıf veya tarih ve saat değeri ve onun ilişkili saat dilimi nesne içeren yapı tanımlamaktır.

. NET'te saat dilimi destek avantajlarını, yalnızca bir tarih ve saat değerini ait olduğu saat dilimini olduğunda bu tarih ve saat nesnesi örneği biliniyorsa mümkündür. Bu genellikle Web veya ağ uygulamaları özellikle de bir durum değildir.

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
