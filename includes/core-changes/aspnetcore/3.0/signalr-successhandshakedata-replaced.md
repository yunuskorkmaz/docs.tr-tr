---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902042"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="5b2a8-101">SignalR: HandshakeProtocol.SuccessHandshakeData değiştirildi</span><span class="sxs-lookup"><span data-stu-id="5b2a8-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="5b2a8-102">[HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) alanı kaldırıldı ve belirli `IHubProtocol`bir verilen başarılı bir el sıkışma yanıtı üreten bir yardımcı yöntemi ile değiştirildi .</span><span class="sxs-lookup"><span data-stu-id="5b2a8-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5b2a8-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="5b2a8-103">Version introduced</span></span>

<span data-ttu-id="5b2a8-104">3,0</span><span class="sxs-lookup"><span data-stu-id="5b2a8-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5b2a8-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="5b2a8-105">Old behavior</span></span>

<span data-ttu-id="5b2a8-106">`HandshakeProtocol.SuccessHandshakeData`bir `public static ReadOnlyMemory<byte>` alandı.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5b2a8-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="5b2a8-107">New behavior</span></span>

<span data-ttu-id="5b2a8-108">`HandshakeProtocol.SuccessHandshakeData`belirtilen protokole dayalı `static` `GetSuccessfulHandshake(IHubProtocol protocol)` bir `ReadOnlyMemory<byte>` döndürür bir yöntem ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5b2a8-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5b2a8-109">Reason for change</span></span>

<span data-ttu-id="5b2a8-110">El sıkışma _yanıtına,_ seçili protokole bağlı olarak sabit olmayan ve değişen ek alanlar eklendi.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5b2a8-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5b2a8-111">Recommended action</span></span>

<span data-ttu-id="5b2a8-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-112">None.</span></span> <span data-ttu-id="5b2a8-113">Bu tür, kullanıcı kodundan kullanım için tasarlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="5b2a8-114">SignalR `public`sunucusu ve istemcisi arasında paylaşılabilsin diye.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="5b2a8-115">.NET'te yazılı müşteri SignalR istemcileri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="5b2a8-116">SignalR **kullanıcıları** bu değişikliktan etkilenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="5b2a8-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="5b2a8-117">Category</span></span>

<span data-ttu-id="5b2a8-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="5b2a8-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5b2a8-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5b2a8-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
