---
title: 'Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf97f1a08c6df13ce639466fc07472926c63987f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106631"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme

Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir. Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir. Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:

- Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.

- Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın. Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.

Bu konu başlığı altında, kullanıcının belirsiz bir süre çözümlenme yöntemi gösterilmektedir.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Kullanıcının belirsiz bir süre çözmesine izin vermek için

1. Kullanıcı tarafından tarih ve saat girişi al.

2. Saatin belirsiz olup olmadığını anlamak için yönteminiçağırın.<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>

3. Süre belirsizse, <xref:System.TimeSpan> nesne dizisini almak için <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> yöntemini çağırın. Dizideki her öğe, belirsiz saatin eşleyebileceğiniz UTC sapmasını içerir.

4. Kullanıcının istenen sapmayı seçmesini sağlayın.

5. Kullanıcı tarafından seçilen sapmayı yerel saatten çıkararak UTC Tarih ve saatini elde edin.

6. `Shared` <xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTime.Kind%2A> UTCTarih<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>ve saat değerinin özelliğini olarak ayarlamak için (VisualBasic.net)metodunuçağırın.`static`

## <a name="example"></a>Örnek

Aşağıdaki örnek, kullanıcıdan bir tarih ve saat girmesini ister ve belirsiz ise kullanıcının belirsiz saatin eşlendiği UTC saatini seçmesini sağlar.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Örnek kodun çekirdeği, UTC 'den belirsiz sürenin olası uzaklıklarını göstermek için bir <xref:System.TimeSpan> nesne dizisi kullanır. Ancak, bu uzaklıklar Kullanıcı için anlamlı değildir. Kaydırmanın anlamını netleştirmek için, kod ayrıca bir uzaklığın yerel saat diliminin standart saatini mi yoksa gün ışığından yararlanma saatini mi temsil ettiğini de not eder. Kod, değeri <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliğin değeriyle karşılaştırarak hangi zamanın standart olduğunu ve ne zaman günışığından yararlanma olduğunu belirler. Bu özellik UTC ve saat diliminin standart saati arasındaki farkı gösterir.

Bu örnekte, yerel saat dilimine yapılan tüm başvurular <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yapılır; yerel saat dilimi hiçbir zaman bir nesne değişkenine atanmaz. Bu önerilen bir uygulamadır çünkü <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı, yerel saat diliminin atandığı tüm nesneleri geçersiz kılar.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- Bu ad alanı, `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir). <xref:System>

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Belirsiz zamanları çözümle](../../../docs/standard/datetime/resolve-ambiguous-times.md)
