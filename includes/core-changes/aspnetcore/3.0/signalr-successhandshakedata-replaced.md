---
ms.openlocfilehash: 05aec429e28ef74515ef6988d5b064e6d16b7c1b
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90680016"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="ed8bd-101">SignalR: HandshakeProtocol. Başarıkıandshakedata değişti</span><span class="sxs-lookup"><span data-stu-id="ed8bd-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="ed8bd-102">[Handshakeprotocol. Fshandshakedata](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) alanı kaldırılmıştır ve belirli bir el sıkışma yanıtı üreten bir yardımcı yöntemle değiştirilmiştir `IHubProtocol` .</span><span class="sxs-lookup"><span data-stu-id="ed8bd-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ed8bd-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ed8bd-103">Version introduced</span></span>

<span data-ttu-id="ed8bd-104">3.0</span><span class="sxs-lookup"><span data-stu-id="ed8bd-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ed8bd-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="ed8bd-105">Old behavior</span></span>

<span data-ttu-id="ed8bd-106">`HandshakeProtocol.SuccessHandshakeData` bir `public static ReadOnlyMemory<byte>` alandır.</span><span class="sxs-lookup"><span data-stu-id="ed8bd-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ed8bd-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="ed8bd-107">New behavior</span></span>

<span data-ttu-id="ed8bd-108">`HandshakeProtocol.SuccessHandshakeData` , `static` `GetSuccessfulHandshake(IHubProtocol protocol)` belirtilen protokole göre döndüren bir yöntemle değiştirilmiştir `ReadOnlyMemory<byte>` .</span><span class="sxs-lookup"><span data-stu-id="ed8bd-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ed8bd-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="ed8bd-109">Reason for change</span></span>

<span data-ttu-id="ed8bd-110">El sıkışma _yanıtına_ , sabit olmayan ve seçilen protokole bağlı olarak değişen ek alanlar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed8bd-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ed8bd-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ed8bd-111">Recommended action</span></span>

<span data-ttu-id="ed8bd-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="ed8bd-112">None.</span></span> <span data-ttu-id="ed8bd-113">Bu tür kullanıcı kodundan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="ed8bd-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="ed8bd-114">Bu `public` , SignalR sunucusu ve istemcisi arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed8bd-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="ed8bd-115">Ayrıca, .NET dilinde yazılmış müşteri SignalR istemcileri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed8bd-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="ed8bd-116">SignalR **kullanıcıları** bu değişiklikten etkilenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="ed8bd-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="ed8bd-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="ed8bd-117">Category</span></span>

<span data-ttu-id="ed8bd-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ed8bd-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ed8bd-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ed8bd-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=nameWithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
