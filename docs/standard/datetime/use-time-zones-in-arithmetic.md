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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 053ca2d10deadf58d5bb8b4628fb5dee815d82c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682699"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma

Normalde, ne zaman, tarih gerçekleştirmek ve aritmetik kullanarak istediğiniz zaman <xref:System.DateTime> veya <xref:System.DateTimeOffset> değerleri, sonucu herhangi bir saat dilimi ayarlama kurallarını yansıtmıyor. Bu tarih ve saat değerinin saat dilimi açıkça tanımlanabilen olsa bile geçerlidir (örneğin, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local>). Bu konuda, belirli bir saat dilimine ait tarih ve saat değerlerini aritmetik işlemleri gösterilmektedir. Aritmetik işlemler sonuçlarını, saat diliminin ayarlama kuralları ücreti yansıtılır.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Tarih ve saat aritmetiği ayarlama kuralları uygulamak için

1. Bir tarih ve saat değerini ait olduğu saat dilimi ile yakından eşlenmesiyle bazı yöntemini uygulayın. Örneğin, hem tarih ve saat değeri hem de saat dilimini içeren bir yapıyı bildirme. Aşağıdaki örnek, bağlamak için bu yaklaşımı kullanır. bir <xref:System.DateTime> kendi saat dilimiyle değeri.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Eşgüdümlü Evrensel Saat (UTC) ya da çağırarak dönüştürün <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> yöntemi veya <xref:System.TimeZoneInfo.ConvertTime%2A> yöntemi.

3. UTC saati aritmetik işlemi gerçekleştirir.

4. Saat, çağırarak orijinal zaman ilişkili saat dilimi UTC'den dönüştürmek <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi.

## <a name="example"></a>Örnek

Aşağıdaki örnek iki saat ve otuz dakika 9 Mart 2008'e 1: 30'da ekler. Merkezi standart saat. Gün ışığından yararlanma saat diliminin geçiş otuz dakika sonra 2: 00'da gerçekleşir. 9 Mart 2008. Örnek önceki bölümde listelenen dört adımları izler olduğundan, sonuçta elde edilen zaman olarak 5: 00'da doğru şekilde rapor 9 Mart 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Her ikisi de <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri ait oldukları tüm zaman dilimine ilişkisi kesilmelidir. Tarih ve saat aritmetiği, otomatik olarak bir saat diliminin ayarlama kuralları uygulayan bir şekilde gerçekleştirmek için hangi bir tüm tarih ve saat değerini ait olduğu saat dilimini hemen tanımlanabilen olması gerekir. Bu, bir tarih ve saat ile ilişkili kendi saat dilimiyle sıkı şekilde bağlı gerekir, anlamına gelir. Aşağıdakiler dahil, bunu yapmanın birkaç yolu vardır:

* Her zaman bir uygulamada kullanılan belirli bir saat dilimine ait varsayılır. Bazı durumlarda uygun olsa da bu yaklaşım sınırlı esnekliği ve büyük olasılıkla sınırlı taşınabilirliği sunar.

* Bir tarih ve saat ekleyerek ilişkili kendi saat dilimiyle hem türünde alanlar olarak sıkı bir şekilde couples bir tür tanımlar. Bu yaklaşım, tarih ve saat ve saat dilimi iki üye alanları depolamak için bir yapı tanımlar kod örneğindeki kullanılır.

Üzerinde aritmetik işlemler gerçekleştirme örnekte gösterildiği <xref:System.DateTime> saat dilimi ayarlama kurallarını sonucu uygulanması değerleri. Ancak, <xref:System.DateTimeOffset> değerleri bir kolayca kullanılabilir. Aşağıdaki örnek nasıl özgün örnek kodu kullanmak için uyarlanmış olabileceği gösterir <xref:System.DateTimeOffset> yerine <xref:System.DateTime> değerleri.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Bu toplama yalnızca gerçekleştirilir gerçekleştiriyorsanız <xref:System.DateTimeOffset> olmadan önce onu UTC'ye dönüştürme, sonucu doğru noktası sürede yansıtır ancak uzaklığı belirtilen saat dilimi, o zaman için yansıtmaz değeri.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.

* Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md)
