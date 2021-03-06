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
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="cd181-103">Socket. LocalEndPoint, SendToAsync çağrıldıktan sonra güncellenir</span><span class="sxs-lookup"><span data-stu-id="cd181-103">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="cd181-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> Şimdi <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> özelliğin değerini yuvanın yerel adresine güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd181-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="cd181-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="cd181-105">Version introduced</span></span>

<span data-ttu-id="cd181-106">5.0</span><span class="sxs-lookup"><span data-stu-id="cd181-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="cd181-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="cd181-107">Change description</span></span>

<span data-ttu-id="cd181-108">Önceki .NET sürümlerinde, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> yuva örneğindeki özelliğin değerini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="cd181-108">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="cd181-109">.NET 5 ' den başlayarak, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> başarıyla tamamlandığında, değeri <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> örtük olarak bağlantılı yuvanın yerel adresidir.</span><span class="sxs-lookup"><span data-stu-id="cd181-109">Starting in .NET 5, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="cd181-110">Bu yeni davranış, ve davranışları ile tutarlıdır <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .</span><span class="sxs-lookup"><span data-stu-id="cd181-110">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="cd181-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="cd181-111">Reason for change</span></span>

<span data-ttu-id="cd181-112">Bu değişiklik [bir hatayı düzeltir](https://github.com/dotnet/runtime/issues/915) ve davranışı çeşitler arasında tutarlı hale getirir `SendTo` .</span><span class="sxs-lookup"><span data-stu-id="cd181-112">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="cd181-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cd181-113">Recommended action</span></span>

<span data-ttu-id="cd181-114">Değerini değiştirmeyeceği varsayan kodu değiştirin <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cd181-114">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="cd181-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cd181-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
