---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394105"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="af385-101">Kerkenez: Boş HTTPS derlemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="af385-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="af385-102">Derleme <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="af385-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="af385-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="af385-103">Version introduced</span></span>

<span data-ttu-id="af385-104">3,0</span><span class="sxs-lookup"><span data-stu-id="af385-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="af385-105">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="af385-105">Reason for change</span></span>

<span data-ttu-id="af385-106">ASP.NET Core 2.1'de `Microsoft.AspNetCore.Server.Kestrel.Https` içeriği <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="af385-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="af385-107">Bu değişiklik öznitelikleri kullanarak `[TypeForwardedTo]` kırılmayan bir şekilde yapıldı.</span><span class="sxs-lookup"><span data-stu-id="af385-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="af385-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="af385-108">Recommended action</span></span>

- <span data-ttu-id="af385-109">2.0'a başvuran `Microsoft.AspNetCore.Server.Kestrel.Https` kitaplıklar, Temel bağımlılıkASP.NET tümASP.NET 2.1 veya sonraki güncelleştirmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="af385-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="af385-110">Aksi takdirde, ASP.NET Core 3.0 uygulamasına yüklendiklerinde kırılabilirler.</span><span class="sxs-lookup"><span data-stu-id="af385-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="af385-111">Core 2.1 ve daha sonra ASP.NET hedefleyen uygulamalar ve `Microsoft.AspNetCore.Server.Kestrel.Https` kütüphaneler NuGet paketine yapılan doğrudan başvuruları kaldırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af385-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="af385-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="af385-112">Category</span></span>

<span data-ttu-id="af385-113">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="af385-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af385-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="af385-114">Affected APIs</span></span>

<span data-ttu-id="af385-115">None</span><span class="sxs-lookup"><span data-stu-id="af385-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
