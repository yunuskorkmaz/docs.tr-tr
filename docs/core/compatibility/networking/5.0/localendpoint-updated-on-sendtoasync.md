---
title: 'Son değişiklik: Socket. LocalEndPoint, SendToAsync çağrıldıktan sonra güncellenir'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinin. SendToAsync, artık yerel uç nokta özelliğinin değerini yuvanın yerel adresine güncelleştirir.
ms.date: 10/18/2020
ms.openlocfilehash: 4be62f8bf6596cc3531d59f3e65eda005bff778a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256432"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a>Socket. LocalEndPoint, SendToAsync çağrıldıktan sonra güncellenir

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> Şimdi <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> özelliğin değerini yuvanın yerel adresine güncelleştirir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> yuva örneğindeki özelliğin değerini değiştirmez. .NET 5 ' den başlayarak, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> başarıyla tamamlandığında, değeri <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> örtük olarak bağlantılı yuvanın yerel adresidir. Bu yeni davranış, ve davranışları ile tutarlıdır <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .

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
