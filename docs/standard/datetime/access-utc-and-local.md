---
title: 'Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106558"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim

Sınıfı, kodunuzun önceden tanımlanmış saat <xref:System.TimeZoneInfo.Utc%2A> dilimi <xref:System.TimeZoneInfo.Local%2A>nesnelerine erişmesini sağlayan iki özellik sağlar. <xref:System.TimeZoneInfo> Bu konu, <xref:System.TimeZoneInfo> bu özellikler tarafından döndürülen nesnelere nasıl erişebileceğinizi anlatmaktadır.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Eşgüdümlü Evrensel Saat (UTC) TimeZoneInfo nesnesine erişmek için

1. Eşgüdümlü Evrensel saate`Shared` erişmek için <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> (Visual Basic) özelliğini kullanın. `static`

2. Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesneyi bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği aracılığıyla Eşgüdümlü Evrensel saate erişmeye devam edin.

### <a name="to-access-the-local-time-zone"></a>Yerel saat dilimine erişmek için

1. Yerel sistem saat`Shared` dilimine erişmek için <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>(VisualBasic ) özelliğini kullanın. `static`

2. Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesneyi bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yerel saat dilimine erişmeye devam edin.

## <a name="example"></a>Örnek

Aşağıdaki kod, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve özelliklerini ABD <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> ve Kanada Doğu Standart saat diliminden bir kez dönüştürmek için ve saat dilimi adını konsola göstermek için kullanır.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Yerel Saat dilimini bir <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo> nesne değişkenine atamak yerine, her zaman, özelliği aracılığıyla yerel saat dilimine erişmeniz gerekir. Benzer şekilde, UTC bölgesini bir <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo> nesne değişkenine atamak yerine, Eşgüdümlü Evrensel saate her zaman özelliği aracılığıyla erişmeniz gerekir. Bu, <xref:System.TimeZoneInfo> nesne değişkeninin <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda yapılan bir çağrı tarafından geçersiz kılınmasını önler.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- Bu ad alanı, `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir). <xref:System>

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md)
