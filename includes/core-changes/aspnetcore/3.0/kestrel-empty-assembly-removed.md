---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394105"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="825ff-101">Kestrel: boş HTTPS derlemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="825ff-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="825ff-102">@No__t-0 derleme kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="825ff-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="825ff-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="825ff-103">Version introduced</span></span>

<span data-ttu-id="825ff-104">3.0</span><span class="sxs-lookup"><span data-stu-id="825ff-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="825ff-105">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="825ff-105">Reason for change</span></span>

<span data-ttu-id="825ff-106">ASP.NET Core 2,1 ' de, `Microsoft.AspNetCore.Server.Kestrel.Https` ' ın içerikleri <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> ' e taşındı.</span><span class="sxs-lookup"><span data-stu-id="825ff-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="825ff-107">Bu değişiklik, `[TypeForwardedTo]` öznitelikleri kullanılarak kırılmamış bir şekilde gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="825ff-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="825ff-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="825ff-108">Recommended action</span></span>

- <span data-ttu-id="825ff-109">@No__t-0 2,0 'e başvuran Kitaplıklar tüm ASP.NET Core bağımlılıklarını 2,1 veya sonraki bir sürüme güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="825ff-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="825ff-110">Aksi takdirde, ASP.NET Core 3,0 uygulamasına yüklendiğinde bu uygulamalar kesintiye uğrabilirler.</span><span class="sxs-lookup"><span data-stu-id="825ff-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="825ff-111">ASP.NET Core 2,1 ve üzeri hedefleme uygulamaları ve kitaplıkları `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet paketine doğrudan başvuruları kaldırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="825ff-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="825ff-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="825ff-112">Category</span></span>

<span data-ttu-id="825ff-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="825ff-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="825ff-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="825ff-114">Affected APIs</span></span>

<span data-ttu-id="825ff-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="825ff-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
