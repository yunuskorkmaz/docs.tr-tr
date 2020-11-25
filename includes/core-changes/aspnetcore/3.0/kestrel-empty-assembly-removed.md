---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032811"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="4d2fb-101">Kestrel: boş HTTPS derlemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="4d2fb-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="4d2fb-102">Derleme <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="4d2fb-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4d2fb-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4d2fb-103">Version introduced</span></span>

<span data-ttu-id="4d2fb-104">3,0</span><span class="sxs-lookup"><span data-stu-id="4d2fb-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4d2fb-105">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4d2fb-105">Reason for change</span></span>

<span data-ttu-id="4d2fb-106">ASP.NET Core 2,1 ' de, içeriği `Microsoft.AspNetCore.Server.Kestrel.Https` öğesine taşındı <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="4d2fb-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="4d2fb-107">Bu değişiklik öznitelikler kullanılarak kırılmamış bir şekilde gerçekleştirildi `[TypeForwardedTo]` .</span><span class="sxs-lookup"><span data-stu-id="4d2fb-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4d2fb-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4d2fb-108">Recommended action</span></span>

- <span data-ttu-id="4d2fb-109">`Microsoft.AspNetCore.Server.Kestrel.Https`2,0 'ye başvuran Kitaplıklar tüm ASP.NET Core bağımlılıklarını 2,1 veya üzeri olarak güncelleştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="4d2fb-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="4d2fb-110">Aksi takdirde, ASP.NET Core 3,0 uygulamasına yüklendiğinde bu uygulamalar kesintiye uğrabilirler.</span><span class="sxs-lookup"><span data-stu-id="4d2fb-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="4d2fb-111">ASP.NET Core 2,1 ve üstünü hedefleyen uygulamalar ve kitaplıklar, NuGet paketine doğrudan başvuruları kaldırmalıdır `Microsoft.AspNetCore.Server.Kestrel.Https` .</span><span class="sxs-lookup"><span data-stu-id="4d2fb-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="4d2fb-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="4d2fb-112">Category</span></span>

<span data-ttu-id="4d2fb-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4d2fb-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4d2fb-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4d2fb-114">Affected APIs</span></span>

<span data-ttu-id="4d2fb-115">Yok</span><span class="sxs-lookup"><span data-stu-id="4d2fb-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
