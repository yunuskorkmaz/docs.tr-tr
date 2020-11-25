---
title: 'Son değişiklik: Socket. LocalEndPoint, SendToAsync çağrıldıktan sonra güncellenir'
description: SendToAsync, artık yerel bitiş noktası özelliğinin değerini yuvanın yerel adresine güncelleştiren .NET 5,0 ' deki kırılmaya karşı değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 53d7da350eac6e65832012331044427fd90fe796
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761442"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a>Socket. LocalEndPoint, SendToAsync çağrıldıktan sonra güncellenir

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> Şimdi <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> özelliğin değerini yuvanın yerel adresine güncelleştirir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> yuva örneğindeki özelliğin değerini değiştirmez. .NET 5,0 ' den başlayarak, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> başarıyla tamamlandığında, değeri <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> örtük olarak bağlantılı yuvanın yerel adresidir. Bu yeni davranış, ve davranışları ile tutarlıdır <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik [bir hatayı düzeltir](https://github.com/dotnet/runtime/issues/915) ve davranışı çeşitler arasında tutarlı hale getirir `SendTo` .

## <a name="recommended-action"></a>Önerilen eylem

Değerini değiştirmeyeceği varsayan kodu değiştirin <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
