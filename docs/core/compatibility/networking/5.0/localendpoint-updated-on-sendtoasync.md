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
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="9c25d-103">Socket. LocalEndPoint, SendToAsync çağrıldıktan sonra güncellenir</span><span class="sxs-lookup"><span data-stu-id="9c25d-103">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="9c25d-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> Şimdi <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> özelliğin değerini yuvanın yerel adresine güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9c25d-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9c25d-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9c25d-105">Version introduced</span></span>

<span data-ttu-id="9c25d-106">5.0</span><span class="sxs-lookup"><span data-stu-id="9c25d-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="9c25d-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="9c25d-107">Change description</span></span>

<span data-ttu-id="9c25d-108">Önceki .NET sürümlerinde, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> yuva örneğindeki özelliğin değerini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="9c25d-108">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="9c25d-109">.NET 5,0 ' den başlayarak, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> başarıyla tamamlandığında, değeri <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> örtük olarak bağlantılı yuvanın yerel adresidir.</span><span class="sxs-lookup"><span data-stu-id="9c25d-109">Starting in .NET 5.0, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="9c25d-110">Bu yeni davranış, ve davranışları ile tutarlıdır <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .</span><span class="sxs-lookup"><span data-stu-id="9c25d-110">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9c25d-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9c25d-111">Reason for change</span></span>

<span data-ttu-id="9c25d-112">Bu değişiklik [bir hatayı düzeltir](https://github.com/dotnet/runtime/issues/915) ve davranışı çeşitler arasında tutarlı hale getirir `SendTo` .</span><span class="sxs-lookup"><span data-stu-id="9c25d-112">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9c25d-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9c25d-113">Recommended action</span></span>

<span data-ttu-id="9c25d-114">Değerini değiştirmeyeceği varsayan kodu değiştirin <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9c25d-114">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9c25d-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9c25d-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
