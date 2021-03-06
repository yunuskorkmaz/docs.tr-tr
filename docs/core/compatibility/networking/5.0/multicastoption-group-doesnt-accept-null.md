---
title: 'Son değişiklik: Multicastop. Group null bir değer kabul etmez'
description: .NET 5 ' teki son değişiklik hakkında daha fazla bilgi edinin. Bu, çok küçük bir değeri artık null bir değer kabul etmez.
ms.date: 08/18/2020
ms.openlocfilehash: 09c6415d275361abee8285aabdda13ccd9727043
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256458"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>Multicastop. Group null bir değer kabul etmez

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> Artık değerini kabul etmez `null` . Özelliğini öğesine ayarlarsanız `null` , bir oluşturulur <xref:System.ArgumentNullException> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 'in önceki sürümlerinde <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> özelliğini olarak ayarlayabilirsiniz `null` . <xref:System.Net.Sockets.MulticastOption>Daha sonra öğesine geçirilirse <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , çalışma zamanı bir oluşturur <xref:System.NullReferenceException> .

.NET 5 ve sonraki sürümlerde, <xref:System.ArgumentNullException> özelliği olarak ayarlarsanız oluşturulur `null` .

## <a name="reason-for-change"></a>Değişiklik nedeni

Framework Tasarım yönergeleriyle tutarlı olması için, özelliği değeri ise oluşturmak üzere güncelleştirilmiştir <xref:System.ArgumentNullException> `null` .

## <a name="recommended-action"></a>Önerilen eylem

' A ayarladığınızdan emin olun <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> `null` .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
