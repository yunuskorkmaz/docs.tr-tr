---
title: Tarih ve saatlerle aritmetik işlemler gerçekleştirme
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2a50823b812541786cf1bebfd6b1262ce2e9314
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070582"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Tarih ve saatlerle aritmetik işlemler gerçekleştirme

Olsa da hem <xref:System.DateTime> ve <xref:System.DateTimeOffset> yapıları değerlerine aritmetik işlemleri üyeleri sağlayabilir, aritmetik işlemler sonuçlarını çok farklıdır. Bu konuda bu farklılıkları inceler, tarih ve saat verilerinin saat dilimini tanıma derece ilgili ve tam olarak kullanarak tarih ve saat verileri saat dilimi kullanan işlemlerini nasıl gerçekleştireceğinizi açıklar.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Koleksiyonlardaki karşılaştırmalar ve DateTime değerlerini içeren aritmetik işlemler

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Özelliği sağlayan bir <xref:System.DateTimeKind> tarih ve saati yerel saat, Eşgüdümlü Evrensel Saat (UTC) veya belirtilmeyen bir saat dilimindeki saati temsil edip etmediğini belirten atanacak değer. Ancak, bu sınırlı saat dilimi bilgilerini karşılaştırma veya tarih ve saat aritmetiği gerçekleştirme göz ardı edilir <xref:System.DateTimeKind> değerleri. Geçerli yerel saat geçerli UTC saati ile karşılaştırır, aşağıdaki örnek bunu göstermektedir.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Yöntemi raporları yerel saat öncesi (veya küçüktür) UTC saati ve çıkarma işlemi gösterir, ABD'deki bir sistem için yerel saati ile UTC arasındaki fark Pasifik Standart saat dilimi yedi saattir. Ancak bu iki değerden zaman tek bir nokta farklı temsilleri sağladığından, bu durumda bu zaman aralığı UTC'den yerel saat diliminin uzaklığı için tamamen ilişkilerinizi temizleyin.

Daha genel <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği tarafından döndürülen sonuçlar etkilemez <xref:System.DateTime.Kind> karşılaştırma ve aritmetik yöntemleri (karşılaştırma zaman iki özdeş noktalar da anlaşılacağı gibi), ancak bu sonuçlar yorumunu etkileyebilir. Örneğin:

* İki tarih ve saat değerleri üzerinde ayarlanmış herhangi bir aritmetik işlemin sonucu gerçekleştirilen <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellikleri eşit <xref:System.DateTimeKind> iki değer arasındaki gerçek zaman aralığını yansıtır. Benzer şekilde, bu iki tarih ve saat değerleri karşılaştırma doğru bir şekilde zamanları arasındaki ilişkiyi yansıtır.

* İki tarih ve saat değerleri üzerinde ayarlanmış herhangi aritmetikte veya Karşılaştırma işleminin sonucu gerçekleştirilen <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellikleri eşit <xref:System.DateTimeKind> veya farklı olan iki tarih ve saat değerlerini <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerleri yansıtır saatin farkı iki değer arasında.

* Belirli bir değeri belirsiz veya geçersiz değil veya yerel saat diliminin geçiş veya gün ışığından yararlanma neden ayarlama kuralları etkisini hesabı yararlanabilir mi yoksa yerel tarih ve saat değerleri üzerinde aritmetikte veya karşılaştırma işlemlerinde düşünün zaman kazandırır.

* Karşılaştırır veya yerel saati ile UTC arasındaki farkı hesaplar herhangi bir işlem sonucu UTC'den yerel saat diliminin uzaklığı için eşit bir zaman aralığı içerir.

* Basit saatin karşılaştırır veya belirtilmeyen bir saat ve UTC veya yerel saat arasındaki farkı hesaplar herhangi bir işlem yansıtır. Saat dilimi farklarını değil olarak değerlendirilir ve sonuç saat dilimi ayarlama kurallarını uygulama yansıtmaz.

* Karşılaştırır veya iki arasındaki farkı hesaplar herhangi bir işlem saatleri, iki farklı saat dilimlerinde saati arasındaki farkı gösteren bir bilinmeyen aralık içerebilir belirtilmemiş.

Hangi saat diliminde farklar tarih ve saat hesaplamaları etkilemez birçok senaryo vardır (bunlardan bazıları için bkz [DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md)) veya, bağlam Tarih ve saat verileri karşılaştırma veya aritmetik işlemleri anlamı tanımlar.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Koleksiyonlardaki karşılaştırmalar ve DateTimeOffset değer aritmetik işlemler

A <xref:System.DateTimeOffset> yalnızca bir tarih ve saat, aynı zamanda bu tarih ve saat UTC'ye göre kesin bir şekilde tanımlayan bir uzaklık değeri içerir. Bu eşitlik için biraz farklı bir biçimde tanımlamak mümkün kılar <xref:System.DateTimeOffset> değerleri. Oysa <xref:System.DateTime> değerler aynı tarih ve saat değeri varsa eşit <xref:System.DateTimeOffset> değerler her ikisi de zaman içinde aynı noktaya başvuruyorsa eşit. Böylece bir <xref:System.DateTimeOffset> daha doğru ve karşılaştırmaları ve iki tarihleri ve saatleri arasındaki aralığı belirlemek çoğu aritmetik işlemler kullanıldığında yorumu geçirilmesi gereken daha az bir değer. Aşağıdaki örnek, <xref:System.DateTimeOffset> UTC ve yerel karşılaştırıldığında önceki örneğe eşdeğerdir <xref:System.DateTimeOffset> değerlerini, bu davranışı farklılık gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Bu örnekte, <xref:System.DateTimeOffset.CompareTo%2A> yöntemi gösterir geçerli yerel saat ve geçerli UTC saatine eşittir ve çıkarılmasının çalıştığını <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> değerleri gösteren iki zaman arasındaki farkı olduğunu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

Kullanmanın baş sınırlama <xref:System.DateTimeOffset> tarih ve saat aritmetiği değerleri olan, ancak <xref:System.DateTimeOffset> değerlere sahip bazı saat dilimini tanıma, bunlar tamamen saat dilimi farkında değildir. Ancak <xref:System.DateTimeOffset> değerinin uzaklığı UTC saat diliminin uzaklığı yansıtan zaman bir <xref:System.DateTimeOffset> değişkenine bir değerin ilk atandığı, saat diliminden bundan sonra ilişkilendirmesi olur. Artık doğrudan tanımlanabilir bir saat ile ilişkili olduğundan, toplama ve çıkarma tarih ve saat aralığı göz önünde bulundurmaz saat diliminin ayarlama kuralları.

Göstermek için gün ışığından yararlanma saatine ABD'deki geçiş Merkezi standart saat dilimi 2: 00'da gerçekleşir 9 Mart 2008. Bu iki ve yarım saat aralığı 1:30 AM Orta Standart Saati için eklediğiniz anlamına gelir 9 Mart 2008'de bir tarih ve saat 5: 00'da, üretmelidir. 9 Mart 2008. Aşağıdaki örnekte gösterildiği gibi ancak ek 4: 00'da sonucudur 9 Mart 2008. Zaman içinde duyuyoruz ilgilenen saat diliminde olmasa da bu bu işlemin sonucunu doğru noktası zamanında temsil Not (diğer bir deyişle, beklenen saat dilimi yok uzaklık).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Saatleri saat diliminde aritmetik işlemler

<xref:System.TimeZoneInfo> Sınıfı bir dizi bunlar saatler bir saat diliminden diğerine dönüştürdüğünüzde, düzeltmeleri otomatik olarak uygulama dönüştürme yöntemleri içerir. Bunlar aşağıdakileri içerir:

* <xref:System.TimeZoneInfo.ConvertTime%2A> Ve <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> saatleri herhangi iki saat dilimleri arasında dönüştürme yöntemleri.

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> Ve <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> belirli bir saat dilimindeki saati UTC'ye dönüştürün ya da belirli bir saat dilimindeki saati UTC'ye dönüştürün yöntemleri.

Ayrıntılar için bkz [saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> Sınıfı, tarih ve saat aritmetiği gerçekleştirdiğinizde ayarlama kuralları otomatik olarak geçerli olan herhangi bir yöntem sağlamaz. Ancak, bir saat dilimindeki saati UTC'ye dönüştürme, aritmetik işlemi gerçekleştiren ve ardından saat dilimindeki saati dön UTC'den dönüştürme bunu yapabilirsiniz. Ayrıntılar için bkz [nasıl yapılır: tarih ve saat aritmetiğinde saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Örneğin, aşağıdaki kod iki-ve-a-yarım saat 2: 00'da için eklenen önceki koda benzer 9 Mart 2008. Ancak, tarih ve saat aritmetiği gerçekleştirir ve ardından sonucu UTC'den merkezi standart saat geri dönüştürür önce merkezi standart saat UTC'ye dönüştürür olduğundan, sonuçta elde edilen zaman merkezi standart saat diliminin gün ışığından geçiş yansıtır saat.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
* [Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
