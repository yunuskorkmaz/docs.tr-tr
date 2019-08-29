---
title: 'Nasıl yapılır: Belirsiz saatleri çözme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e98d5d8240492ca30da2825b72277d7a35f97f6
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106777"
---
# <a name="how-to-resolve-ambiguous-times"></a>Nasıl yapılır: Belirsiz saatleri çözme

Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir. Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir. Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:

- Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın. Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.

- Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.

Bu konuda, saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın nasıl çözümleneceği gösterilmektedir.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Belirsiz bir süreyi saat diliminin standart saatine eşlemek için

1. Saatin belirsiz olup olmadığını anlamak için yönteminiçağırın.<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>

2. Zaman belirsiz ise, saat <xref:System.TimeSpan> <xref:System.TimeZoneInfo.BaseUtcOffset%2A> dilimi özelliği tarafından döndürülen nesneden saati çıkarın.

3. `Shared` <xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTime.Kind%2A> UTCTarih<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>ve saat değerinin özelliğini olarak ayarlamak için (VisualBasic.net)metodunuçağırın.`static`

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın UTC 'ye nasıl dönüştürüleceğini gösterir.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Örnek, geçirilen <xref:System.DateTime> değerin belirsiz olup olmadığını `ResolveAmbiguousTime` belirleyen adlı bir yöntemden oluşur. Değer belirsiz ise, yöntemi karşılık gelen UTC zamanını temsil <xref:System.DateTime> eden bir değer döndürür. Yöntemi, yerel saat dilimi <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliğinin değerini yerel saatten çıkararak bu dönüştürmeyi işler.

Normalde belirsiz bir zaman, belirsiz zamanın olası UTC uzaklıklarını içeren bir <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> <xref:System.TimeSpan> nesne dizisini almak için yöntemini çağırarak işlenir. Ancak bu örnek, belirsiz bir saatin, her zaman saat diliminin standart saatine eşlenmesi gereken rastgele varsayımını yapar. <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Özelliği UTC ve saat diliminin standart saati arasındaki sapmayı döndürür.

Bu örnekte, yerel saat dilimine yapılan tüm başvurular <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yapılır; yerel saat dilimi hiçbir zaman bir nesne değişkenine atanmaz. Bu önerilen bir uygulamadır çünkü <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı, yerel saat diliminin atandığı tüm nesneleri geçersiz kılar.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- Bu ad alanı, `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir). <xref:System>

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Kullanıcıların belirsiz zamanları çözmesine izin ver](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
