---
title: 'Nasıl yapılır: belirsiz zamanları çözme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 0b5b28c588237fb2f7f069aaef06f3f73d5268bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122244"
---
# <a name="how-to-resolve-ambiguous-times"></a>Nasıl yapılır: belirsiz zamanları çözme

Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir. Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir. Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:

- Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın. Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.

- Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.

Bu konuda, saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın nasıl çözümleneceği gösterilmektedir.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Belirsiz bir süreyi saat diliminin standart saatine eşlemek için

1. Saatin belirsiz olup olmadığını anlamak için <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> yöntemini çağırın.

2. Zaman belirsiz ise, saat diliminin <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği tarafından döndürülen <xref:System.TimeSpan> nesnesinden saati çıkarın.

3. UTC Tarih ve saat değerinin <xref:System.DateTime.Kind%2A> özelliğini ayarlamak için `static` (Visual Basic .NET 'te`Shared`) <xref:System.DateTime.SpecifyKind%2A> yöntemini çağırın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın UTC 'ye nasıl dönüştürüleceğini gösterir.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Örnek, geçirilen <xref:System.DateTime> değerinin belirsiz olup olmadığını belirleyen `ResolveAmbiguousTime` adlı bir yöntemden oluşur. Değer belirsiz ise, yöntemi karşılık gelen UTC zamanını temsil eden bir <xref:System.DateTime> değer döndürür. Yöntemi, yerel saat diliminin <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliğinin değerini yerel saatten çıkararak bu dönüştürmeyi işler.

Normalde belirsiz bir zaman, belirsiz zamanın olası UTC uzaklıklarını içeren bir dizi <xref:System.TimeSpan> nesne almak için <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> yöntemi çağırarak işlenir. Ancak bu örnek, belirsiz bir saatin, her zaman saat diliminin standart saatine eşlenmesi gereken rastgele varsayımını yapar. <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği UTC ile saat diliminin standart saati arasındaki sapmayı döndürür.

Bu örnekte, yerel saat dilimine yapılan tüm başvurular <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yapılır; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz. Bu önerilen bir uygulamadır çünkü <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı, yerel saat diliminin atandığı nesneleri geçersiz kılar.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- <xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
