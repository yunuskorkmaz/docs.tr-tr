---
title: "DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçme"
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
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f9a91f7a00f72917ca5c469f51fd0aa11e24e125
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçme

Tarih ve saat bilgilerini kullanan .NET uygulamaları çok çeşitli ve bu bilgileri çeşitli yollarla kullanabilirsiniz. Aşağıdakilerden birini veya birkaçını tarih ve saat bilgilerini daha yaygın kullanımları şunlardır:

* Yalnızca bir tarih yansıtmak için bu nedenle bu saat bilgisi önemli değildir.

* Yalnızca bir kez yansıtmak için bu nedenle bu tarih bilgisi önemli değildir.

* Bir Özet tarih ve belirli bir zaman ve yerde (örneğin, çoğu mağazasında hafta içi günlerde saat 9: 00'da açık bir Uluslararası zinciri) bağlanmayan saat yansıtacak şekilde.

* .NET dışında kaynaklardan tarih ve saat bilgilerini almak için genellikle basit bir tarih ve saat bilgilerini depolandığı veri türü.

* Benzersiz ve belirsizliğe tek bir nokta sürede belirlemek için. Bazı uygulamalar, bir tarih ve saat yalnızca ana bilgisayar sisteminde benzersiz olmasını gerektirir; Başkalarının bu sistemlerden benzersiz olmasını gerektirir (diğer bir deyişle, tek bir sisteme seri hale getirilmiş bir tarih anlamlı serisi ve dünyanın başka bir sistem üzerinde kullanılan).

* Birden çok korumak için (örneğin, istek sahibinin yerel saat ve Web isteği giriş sunucu saati) saatleri ilgili.

* Tarih ve saat gerçekleştirmek için büyük olasılıkla bir sonuçla aritmetik, benzersiz olarak ve belirsizliğe tek bir nokta zamanında tanımlar.

.NET içeren <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, ve <xref:System.TimeZoneInfo> türleri, bunların tümü olduğu tarih ve saatlerle çalışan uygulamaları oluşturmak için kullanılabilir.

> [!NOTE]
> Bu konu, dördüncü bir Türü tartışılmaz <xref:System.TimeZone>işlevselliğini neredeyse tamamen eklenmiştir çünkü <xref:System.TimeZoneInfo> sınıfı. Mümkün olduğunda, geliştiriciler kullanmalıdır <xref:System.TimeZoneInfo> sınıfının yerine <xref:System.TimeZone> sınıfı.

## <a name="the-datetime-structure"></a>DateTime yapısı

A <xref:System.DateTime> belirli bir tarih ve saat değeri tanımlar. İçerdiği bir <xref:System.DateTime.Kind%2A> sağlar özelliği sınırlı hangi saat dilimi bilgilerini bu tarih ve saat ait. <xref:System.DateTimeKind> Tarafından döndürülen değer <xref:System.DateTime.Kind%2A> özelliği gösterir olup olmadığını <xref:System.DateTime> değeri yerel saat temsil eder (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Eşgüdümlü Evrensel Saat (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), ya da belirsiz bir süre (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

<xref:System.DateTime> Yapısıdır aşağıdakileri uygulamaları için uygundur:

* Yalnızca tarih ile çalışır.

* Yalnızca süreleri ile çalışır.

* Soyut tarih ve saatlerle çalışır.

* Tarihler ve saatler için hangi saat dilimi bilgileri eksik çalışın.

* UTC tarihleri ve saatlerle yalnızca çalışır.

* SQL veritabanları gibi .NET dışında kaynaklardan tarih ve saat bilgilerini alır. Genellikle, bu kaynakları ile uyumlu basit bir biçimde tarih ve saat bilgilerini saklar <xref:System.DateTime> yapısı.

* Tarih gerçekleştirin ve saat aritmetiğinde kullanılır ancak genel sonuçları ilgilenir. Örneğin, belirli bir tarih ve saat için altı ay ekler bir toplama işleminde, bu sonucu ışığından olup ayarlanır önemli çoğunlukla değildir.

Sürece belirli bir <xref:System.DateTime> değerini temsil eder, UTC bu tarih ve saat değeri genellikle belirsiz veya kendi taşınabilirliği sınırlı. Örneğin, bir <xref:System.DateTime> değeri yerel saat temsil eder, (diğer bir deyişle, değer aynı saat diliminde değer zamanında hala belirsizliğe tek bir nokta tanımlar, başka bir sistem üzerindeki seri durumdan olan), yerel saat dilimi içinde taşınabilir. Yerel saat dilimi dışında <xref:System.DateTime> değeri birden çok yorumlar sahip olabilir. Varsa değerinin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, daha az taşınabilir: Bunu şimdi aynı saat diliminde içinde ve büyük olasılıkla üzerinde ilk duruma getirildi bile aynı sistemde belirsiz. Yalnızca bir <xref:System.DateTime> değeri değeri belirsizliğe tek bir nokta sistem veya saat dilimi değeri kullanıldığından bağımsız olarak zaman içinde tanımladıkları UTC mu temsil eder.

> [!IMPORTANT]
> Paylaşımı veya kaydederken <xref:System.DateTime> veri, UTC kullanılmalıdır ve <xref:System.DateTime> değerinin <xref:System.DateTime.Kind%2A> özelliği ayarlanmalıdır <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset yapısı

<xref:System.DateTimeOffset> Yapısı ne kadar bu değer UTC farklı gösteren uzaklığı birlikte tarih ve saat bir değeri temsil eder. Bu nedenle, değer her zaman belirsizliğe zamanında tek bir nokta tanımlar.

<xref:System.DateTimeOffset> Türünü içeren tüm işlevselliğini <xref:System.DateTime> saat dilimi tanıma birlikte türü. Bu aşağıdakileri uygulamalar için uygun hale getirir:

* Benzersiz ve belirsizliğe tek bir nokta zamanında belirleyin. <xref:System.DateTimeOffset> Türü, sistem veya uygulama olayları sürelerinin günlüğe kaydetmek için "Şimdi", günlük işlem süreleri ve kayıt dosyası oluşturma ve değiştirme kez anlamını belirsizliğe tanımlamak için kullanılabilir.

* Genel tarih ve saat aritmetiğinde gerçekleştirin.

* Birden çok korumak bu kez iki ayrı değeri veya iki bir yapı üyeleri olarak depolanan sürece kez ilgili.

> [!NOTE]
> Bu kullanımları <xref:System.DateTimeOffset> değerler için olandan çok daha yaygın <xref:System.DateTime> değerleri. Sonuç olarak, <xref:System.DateTimeOffset> uygulama geliştirme için varsayılan tarih ve saat türü düşünülmelidir.

A <xref:System.DateTimeOffset> değer belirli bir zaman dilimine bağlı değildir, ancak herhangi bir saat dilimleri çeşitli kaynaklanan. Aşağıdaki örnekte bu göstermek için hangi saat dilimleri listeler bir dizi <xref:System.DateTimeOffset> (bir yerel Pasifik Standart Saati dahil) değerleri ait.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Çıktı, her tarihi gösterir ve en az üç farklı saat dilimleri için saat değeri bu örnekte ait olabilir. <xref:System.DateTimeOffset> 10/6/2007 değerini gösteren bir tarih ve saat değeri gün ışığından yararlanma saati temsil ediyorsa, kendi UTC uzaklığı bile gerekmez kaynak saat diliminin temel UTC uzaklığı veya görünen adını bulunan UTC uzaklığı karşılık geldiğinden emin. Bu, çünkü anlamına tek bir <xref:System.DateTimeOffset> değeri değil sıkı şekilde bağlı kendi saat dilimi ile bir saat diliminin gün ışığından yararlanma saati gelen ve giden geçiş yansıtacak olamaz. Tarih ve saat aritmetiği kullanıldığında işlemek için bu özellikle sorunlu olabilir bir <xref:System.DateTimeOffset> değeri. (Bir tarih ve saat aritmetiği bir saat diliminin ayarlama kuralları hesabı götüren bir şekilde gerçekleştirmek nasıl tartışma için bkz: [tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>TimeSpan yapısı

<xref:System.TimeSpan> Yapısı bir zaman aralığı temsil eder. İki tipik kullanımları şunlardır:

* İki tarih ve saat değerleri arasındaki zaman aralığını yansıtma. Örneğin, bir çıkarılmasıyla <xref:System.DateTime> başka bir döndürür değerinden bir <xref:System.TimeSpan> değeri.

* Ölçüm geçen süre. Örneğin, <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.TimeSpan> birini çağrısından itibaren geçen zaman aralığını yansıtır değeri <xref:System.Diagnostics.Stopwatch> geçen süreyi ölçmek için başlar yöntemleri.

A <xref:System.TimeSpan> değeri de kullanılabilir yerini almak üzere bir <xref:System.DateTime> değer olduğunda bu değeri günün belirli bir zamanda başvuru olmadan verilerdir. Bu kullanım benzer <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> dönüş özellikleri bir <xref:System.TimeSpan> bir tarih başvuru olmadan saati gösteren bir değer. Örneğin, <xref:System.TimeSpan> yapısı, bir mağaza günlük açma veya kapatma süresi yansıtmak için kullanılabilir veya herhangi bir normal olayın gerçekleştiği zaman temsil etmek için kullanılabilir.

Aşağıdaki örnek tanımlar bir `StoreInfo` içerir yapısı <xref:System.TimeSpan> nesneleri için depolama açma ve kapatma süreleri yanı sıra bir <xref:System.TimeZoneInfo> mağaza saat dilimini temsil eden nesne. Yapısı iki yöntem de içerir `IsOpenNow` ve `IsOpenAt`, mağaza kimin yerel saat diliminde olduğu varsayılır kullanıcı tarafından belirtilen bir zamanda açık olup olmadığını gösterir.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Yapısı kullanılabilecek istemci kodu aşağıdaki gibi tarafından.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>Timezoneınfo sınıfı

<xref:System.TimeZoneInfo> Sınıfı dünya saat dilimleri birini temsil eder ve tüm tarih ve saati bir saat diliminde dönüştürülmesi başka bir saat diliminde eşdeğerine sağlar. <xref:System.TimeZoneInfo> Sınıfı tarihleri ile çalışmak mümkün hale getirir ve herhangi bir tarih ve saat değeri tek bir nokta zamanında belirsizliğe yer bırakmadan tanımlar. böylece zaman. <xref:System.TimeZoneInfo> Sınıftır da genişletilebilir. Windows sistemlerinde sağlandığını ve kayıt defterinde tanımlanan saat dilimi bilgileri bağlı olsa da, özel saat dilimlerini oluşturulmasını destekler. Serileştirme ve seri durumdan çıkarma işlemi saat dilimi bilgilerini de destekler.

Bazı durumlarda, tam yararlanarak <xref:System.TimeZoneInfo> sınıfı, başka geliştirme iş gerektirebilir. Tarih ve saat değerlerini birbirine sıkı şekilde zaman hangi bunlar ait, daha fazla iş bölgeleri ile bağlı değil ise gereklidir. Uygulamanızı bir tarih ve saat, ilişkili saat dilimi ile bağlama için bazı mekanizma sağlar sürece, belirli bir tarih ve saat değeri kendi saat diliminden ilişkilendirmesi hale daha kolay olur. Bu bilgileri bağlama bir yöntemi, bir sınıf veya tarih ve saat değeri ile ilişkili saat dilimi nesne içeren yapısı tanımlamaktır.

.NET ile saat dilimi destek yararlanarak, yalnızca bir tarih ve saat değeri ait olduğu saat dilimi, ne zaman bu tarih ve saat nesne örneği biliniyorsa mümkündür. Bu genellikle durumda, özellikle Web veya ağ uygulamaları değildir.

## <a name="see-also"></a>Ayrıca bkz.

[Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
