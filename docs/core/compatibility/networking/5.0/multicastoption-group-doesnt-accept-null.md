---
title: 'Son değişiklik: Multicastop. Group null bir değer kabul etmez'
description: Çok kanallı bir değeri artık boş bir değer kabul etmeyen .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761438"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>Multicastop. Group null bir değer kabul etmez

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> Artık değerini kabul etmez `null` . Özelliğini öğesine ayarlarsanız `null` , bir oluşturulur <xref:System.ArgumentNullException> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 'in önceki sürümlerinde <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> özelliğini olarak ayarlayabilirsiniz `null` . <xref:System.Net.Sockets.MulticastOption>Daha sonra öğesine geçirilirse <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , çalışma zamanı bir oluşturur <xref:System.NullReferenceException> .

.NET 5,0 ve üzeri sürümlerde, <xref:System.ArgumentNullException> özelliği olarak ayarlarsanız oluşturulur `null` .

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
