---
title: 'Nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9d326750cdef96be1aa6055d46b4ac08ec7a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574588"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır

Normalde, zaman, tarih gerçekleştirmek ve aritmetik kullanarak istediğiniz zaman <xref:System.DateTime> veya <xref:System.DateTimeOffset> değerleri, sonuç tüm saat dilimi ayarlama kuralları yansıtır değil. Bu tarih ve saat değerinin saat dilimi açıkça tanımlanabilen olsa bile geçerlidir (örneğin, <xref:System.DateTime.Kind%2A> özelliği ayarlanmış <xref:System.DateTimeKind.Local>). Bu konuda, belirli bir saat dilimine ait tarih ve saat değerleri aritmetik işlemleri gösterilmektedir. Aritmetik işlemler sonuçlarını saat diliminin ayarlama kuralları yansıtır.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Tarih ve saat aritmetiği ayarlama kuralları uygulamak için

1. Tarih ve saat değeri ait olduğu saat dilimi ile yakından Kuplaj bazı yöntemini uygulayın. Örneğin, tarih ve saat değeri ile kendi saat dilimi içeren bir yapıyı bildirme. Aşağıdaki örnek, bağlamak için bu yaklaşımı kullanır. bir <xref:System.DateTime> değeri, saat dilimi ile.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Bir saat ya da çağırarak Eşgüdümlü Evrensel Saat (UTC) dönüştürmek <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> yöntemi veya <xref:System.TimeZoneInfo.ConvertTime%2A> yöntemi.

3. UTC saati aritmetik işlemi gerçekleştirin.

4. Saati UTC özgün zaman ilişkili saat dilimi çağırarak Dönüştür <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi.

## <a name="example"></a>Örnek

Aşağıdaki örnek 9 Mart 2008'e iki saat ve otuz dakika, 1: 30'da ekler. Orta Standart Saati. Saat diliminin gün ışığından yararlanma saati geçiş otuz dakika sonra 2: 00'da gerçekleşir. 9 Mart 2008'de. Örnek önceki bölümde listelenen dört adımdan oluşur olduğundan, sonuçta elde edilen zaman olarak 5: 00'da doğru şekilde rapor 9 Mart 2008'de.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Her ikisi de <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri ait oldukları her saat diliminden ilişkisi. Tarih ve saat aritmetiği bir saat diliminin ayarlama kuralları otomatik olarak uygulanan bir şekilde gerçekleştirmek için hangi bir tüm tarih ve saat değeri ait saat dilimi hemen tanımlanabilen olması gerekir. Bu, bir tarih ve saat ve onun ilişkili saat dilimi sıkı şekilde bağlı gerekir, anlamına gelir. Aşağıdakiler dahil Bunu yapmak için birkaç yolu vardır:

* Her zaman bir uygulamada kullanılan belirli bir saat dilimine ait varsayalım. Bazı durumlarda uygun olsa da bu yaklaşım sınırlı esneklik ve büyük olasılıkla sınırlı taşınabilirlik sunar.

* Bir tarih ve saat ekleyerek ilişkili kendi saat dilimi ile iki tür alanları olarak sıkı bir şekilde couples bir türünü tanımlayın. Bu yaklaşım, tarih ve saat ve saat dilimi iki üye alanlarında depolamak için bir yapısını tanımlar kod örneğindeki kullanılır.

Örnek üzerinde aritmetik işlemler gerçekleştirmek nasıl gösterilmektedir <xref:System.DateTime> saat dilimi ayarlama kuralları sonucu uygulanan böylece değerleri. Ancak, <xref:System.DateTimeOffset> değerleri kolayca kullanılabilir. Aşağıdaki örnekte, nasıl özgün örnekteki kod kullanmak için uyarlanmış olabileceği gösterilmektedir <xref:System.DateTimeOffset> yerine <xref:System.DateTime> değerleri.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Bu ek yalnızca gerçekleştirilirse unutmayın <xref:System.DateTimeOffset> ilk sonuç doğru noktası zamanında yansıtır UTC'ye dönüştürme, ancak kendi uzaklık belirtilen saat dilimi, o zaman için yansıtmaz olmadan değeri.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Core.dll projeye eklenmesini.

* Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md)
