---
title: 'Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma'
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
ms.openlocfilehash: af19145f7caa9dbe8630ae7593734769e98720d0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280926"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma

Genellikle, veya değerlerini kullanarak tarih ve saat aritmetiği gerçekleştirdiğinizde <xref:System.DateTime> <xref:System.DateTimeOffset> , sonuç hiçbir saat dilimi ayarlama kuralını yansıtmaz. Bu, tarih ve saat değerinin saat dilimi açıkça tanımlanabilir olsa da (örneğin, <xref:System.DateTime.Kind%2A> özellik olarak ayarlandığında <xref:System.DateTimeKind.Local> ) geçerlidir. Bu konu, belirli bir saat dilimine ait tarih ve saat değerleri üzerinde aritmetik işlemlerin nasıl gerçekleştirileceğini gösterir. Aritmetik işlemlerin sonuçları, saat diliminin ayarlama kurallarını yansıtır.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Tarih ve saat aritmetiğinin ayarlama kurallarını uygulamak için

1. Bir tarih ve saat değerini, ait olduğu saat dilimiyle bir daha yakından eşlenme yöntemini uygulayın. Örneğin, hem tarih hem de saat değerini ve saat dilimini içeren bir yapı bildirin. Aşağıdaki örnek, bir <xref:System.DateTime> değeri saat dilimiyle bağlamak için bu yaklaşımı kullanır.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Yöntemini ya da yöntemini çağırarak bir saati Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürün <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> <xref:System.TimeZoneInfo.ConvertTime%2A> .

3. Aritmetik işlemi UTC saat üzerinde gerçekleştirin.

4. Yöntemini çağırarak UTC 'den ilk saatin ilişkili saat dilimine Dönüştür <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, 9 Mart 2008 ' de saat 1:30 ' de 2 saat ve otuz dakika ekler. Merkezi Standart Saati. Saat diliminin gün ışığından yararlanma saatine geçiş süresi otuz dakika sonra, 2:00 saat 9 Mart 2008 ' de. Örnek, önceki bölümde listelenen dört adımı takip ettiğinden, sonuç süresini 5:00 olarak doğru şekilde bildiriyor 9 Mart 2008 ' de.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Hem hem de <xref:System.DateTime> <xref:System.DateTimeOffset> değerlerinin ait oldukları herhangi bir saat diliminden ilişkisi kaldırılır. Tarih ve saat aritmetiğini otomatik olarak bir saat dilimi ayarlama kuralları uygulayan bir şekilde gerçekleştirmek için, herhangi bir tarih ve saat değerinin ait olduğu saat dilimi hemen tanınabilir olmalıdır. Bu, bir tarih ve saatin ve ilişkili saat diliminin sıkı bir şekilde bağlanmış olması gerektiği anlamına gelir. Bunu yapmak için aşağıdakiler dahil olmak üzere çeşitli yollar vardır:

- Bir uygulamada kullanılan tüm saatlerin belirli bir saat dilimine ait olduğunu varsayın. Bazı durumlarda uygun olsa da, bu yaklaşım sınırlı esneklik ve muhtemelen sınırlı taşınabilirlik sağlar.

- Her iki türü de dahil olmak üzere, bir tarih ve saati ilişkili saat dilimiyle sıkı bir şekilde birbirine bağlayan bir tür tanımlayın. Bu yaklaşım, tarih ve saat ve saat dilimini iki üye alanında depolamak için bir yapıyı tanımlayan kod örneğinde kullanılır.

Örnek, <xref:System.DateTime> saat dilimi ayarlama kurallarının sonuca uygulanması için değerler üzerinde aritmetik işlemlerin nasıl gerçekleştirileceğini gösterir. Ancak, <xref:System.DateTimeOffset> değerler yalnızca kolayca kullanılabilir. Aşağıdaki örnek, özgün örnekteki kodun değer yerine kullanılacak şekilde nasıl uyarlandığını gösterir <xref:System.DateTimeOffset> <xref:System.DateTime> .

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Bu ekleme işlemi <xref:System.DateTimeOffset> önce UTC 'ye dönüştürülürken değer üzerinde gerçekleştirildiğinde, sonuç doğru noktayı yansıtır, ancak bu süre için belirlenen saat dilimini göstermez.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Tarih ve saatlerle aritmetik işlemler gerçekleştirme](performing-arithmetic-operations.md)
