---
title: 'Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma'
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
ms.openlocfilehash: 1acd53fad6b0ab173f855850353339190ebdd893
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132535"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma

Genellikle, <xref:System.DateTime> veya <xref:System.DateTimeOffset> değerlerini kullanarak tarih ve saat aritmetiği gerçekleştirdiğinizde, sonuç hiçbir saat dilimi ayarlama kuralını yansıtmaz. Bu, tarih ve saat değerinin saat dilimi açıkça tanımlanabilir olsa da (örneğin, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local>olarak ayarlandığında) geçerlidir. Bu konu, belirli bir saat dilimine ait tarih ve saat değerleri üzerinde aritmetik işlemlerin nasıl gerçekleştirileceğini gösterir. Aritmetik işlemlerin sonuçları, saat diliminin ayarlama kurallarını yansıtır.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Tarih ve saat aritmetiğinin ayarlama kurallarını uygulamak için

1. Bir tarih ve saat değerini, ait olduğu saat dilimiyle bir daha yakından eşlenme yöntemini uygulayın. Örneğin, hem tarih hem de saat değerini ve saat dilimini içeren bir yapı bildirin. Aşağıdaki örnek, bir <xref:System.DateTime> değerini saat dilimiyle bağlamak için bu yaklaşımı kullanır.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> yöntemini ya da <xref:System.TimeZoneInfo.ConvertTime%2A> yöntemini çağırarak bir saati Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürün.

3. Aritmetik işlemi UTC saat üzerinde gerçekleştirin.

4. <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemini çağırarak UTC 'den ilk saatin ilişkili saat dilimine dönüştürme.

## <a name="example"></a>Örnek

Aşağıdaki örnek, 9 Mart 2008 ' de saat 1:30 ' de 2 saat ve otuz dakika ekler. Merkezi Standart Saati. Saat diliminin gün ışığından yararlanma saatine geçiş süresi otuz dakika sonra, 2:00 saat 9 Mart 2008 ' de. Örnek, önceki bölümde listelenen dört adımı takip ettiğinden, sonuç süresini 5:00 olarak doğru şekilde bildiriyor 9 Mart 2008 ' de.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<xref:System.DateTime> ve <xref:System.DateTimeOffset> değerlerinin, ait oldukları herhangi bir saat diliminden ilişkisi kaldırılır. Tarih ve saat aritmetiğini otomatik olarak bir saat dilimi ayarlama kuralları uygulayan bir şekilde gerçekleştirmek için, herhangi bir tarih ve saat değerinin ait olduğu saat dilimi hemen tanınabilir olmalıdır. Bu, bir tarih ve saatin ve ilişkili saat diliminin sıkı bir şekilde bağlanmış olması gerektiği anlamına gelir. Bunu yapmak için aşağıdakiler dahil olmak üzere çeşitli yollar vardır:

- Bir uygulamada kullanılan tüm saatlerin belirli bir saat dilimine ait olduğunu varsayın. Bazı durumlarda uygun olsa da, bu yaklaşım sınırlı esneklik ve muhtemelen sınırlı taşınabilirlik sağlar.

- Her iki türü de dahil olmak üzere, bir tarih ve saati ilişkili saat dilimiyle sıkı bir şekilde birbirine bağlayan bir tür tanımlayın. Bu yaklaşım, tarih ve saat ve saat dilimini iki üye alanında depolamak için bir yapıyı tanımlayan kod örneğinde kullanılır.

Örnek, zaman dilimi ayarlama kurallarının sonuca uygulanması için <xref:System.DateTime> değerler üzerinde aritmetik işlemlerin nasıl gerçekleştirileceğini gösterir. Ancak, <xref:System.DateTimeOffset> değerleri yalnızca kolayca kullanılabilir. Aşağıdaki örnek, özgün örnekteki kodun <xref:System.DateTime> değerleri yerine <xref:System.DateTimeOffset> kullanmak için nasıl uyarlandığını gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Bu ekleme işlemi ilk olarak UTC 'ye dönüştürmeden <xref:System.DateTimeOffset> değer üzerinde gerçekleştirildiğinde, sonuç doğru noktayı yansıtır, ancak bu süre için belirlenen saat dilimini göstermez.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- <xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md)
