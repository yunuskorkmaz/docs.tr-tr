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
ms.openlocfilehash: ebb07800b2a35f4faf312dc55b8c5679079b4b68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291415"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim

<xref:System.TimeZoneInfo>Sınıfı, <xref:System.TimeZoneInfo.Utc%2A> <xref:System.TimeZoneInfo.Local%2A> kodunuzun önceden tanımlanmış saat dilimi nesnelerine erişmesini sağlayan iki özellik sağlar. Bu konu, bu <xref:System.TimeZoneInfo> Özellikler tarafından döndürülen nesnelere nasıl erişebileceğinizi anlatmaktadır.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Eşgüdümlü Evrensel Saat (UTC) TimeZoneInfo nesnesine erişmek için

1. `static` `Shared` <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Eşgüdümlü Evrensel saate erişmek için (Visual Basic) özelliğini kullanın.

2. <xref:System.TimeZoneInfo>Özelliği tarafından döndürülen nesneyi bir nesne değişkenine atamak yerine, özelliği aracılığıyla Eşgüdümlü Evrensel saate erişmeye devam edin <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> .

### <a name="to-access-the-local-time-zone"></a>Yerel saat dilimine erişmek için

1. `static` `Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Yerel sistem saat dilimine erişmek için (Visual Basic) özelliğini kullanın.

2. <xref:System.TimeZoneInfo>Özelliği tarafından döndürülen nesneyi bir nesne değişkenine atamak yerine, özelliği aracılığıyla yerel saat dilimine erişmeye devam edin <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> .

## <a name="example"></a>Örnek

Aşağıdaki kod, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliklerini ABD ve Kanada Doğu Standart saat diliminden bir kez dönüştürmek için ve saat dilimi adını konsola göstermek için kullanır.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Yerel Saat dilimini <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> bir nesne değişkenine atamak yerine, her zaman, özelliği aracılığıyla yerel saat dilimine erişmeniz gerekir <xref:System.TimeZoneInfo> . Benzer şekilde, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC bölgesini bir nesne değişkenine atamak yerine, Eşgüdümlü Evrensel saate her zaman özelliği aracılığıyla erişmeniz gerekir <xref:System.TimeZoneInfo> . Bu, <xref:System.TimeZoneInfo> nesne değişkeninin metoda yapılan bir çağrı tarafından geçersiz kılınmasını önler <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> .

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](finding-the-time-zones-on-local-system.md)
- [Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma](instantiate-time-zone-info.md)
