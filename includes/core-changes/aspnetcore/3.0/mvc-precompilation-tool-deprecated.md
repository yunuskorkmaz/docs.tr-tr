---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901749"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="1a44c-101">MVC: Precompilation aracı amortismana</span><span class="sxs-lookup"><span data-stu-id="1a44c-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="1a44c-102">Core 1.1ASP.NETde, `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation aracı) paketi Razor dosyalarının yayımlama zamanı derlemesi *(.cshtml* dosyaları) için destek eklemek için tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="1a44c-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="1a44c-103">Core 2.1ASP.NET [de, Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) precompilation aracının özellikleri üzerine genişletmek için tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="1a44c-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="1a44c-104">Razor SDK, Razor dosyalarının oluşturma ve yayımlama zamanı derlemesi için destek ekledi.</span><span class="sxs-lookup"><span data-stu-id="1a44c-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="1a44c-105">SDK, *.cshtml* dosyalarının oluşturma zamanında doğruluğunu doğrularken, uygulama başlangıç zamanında iyileşir.</span><span class="sxs-lookup"><span data-stu-id="1a44c-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="1a44c-106">Razor SDK varsayılan olarak açıktır ve kullanmaya başlamak için herhangi bir hareket gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1a44c-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="1a44c-107">Core 3.0ASP.NETde, ASP.NET Core 1.1-era MVC precompilation aracı kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="1a44c-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="1a44c-108">Önceki paket sürümleri yama sürümünde önemli hata ve güvenlik düzeltmeleri almaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="1a44c-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1a44c-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="1a44c-109">Version introduced</span></span>

<span data-ttu-id="1a44c-110">3,0</span><span class="sxs-lookup"><span data-stu-id="1a44c-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1a44c-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="1a44c-111">Old behavior</span></span>

<span data-ttu-id="1a44c-112">Paket, `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` MVC Razor görünümlerini önceden derlemek için kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1a44c-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1a44c-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="1a44c-113">New behavior</span></span>

<span data-ttu-id="1a44c-114">Razor SDK bu işlevselliği doğal olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="1a44c-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="1a44c-115">Paket `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` artık güncelleştirdeğil.</span><span class="sxs-lookup"><span data-stu-id="1a44c-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1a44c-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="1a44c-116">Reason for change</span></span>

<span data-ttu-id="1a44c-117">Razor SDK daha fazla işlevsellik sağlar ve *.cshtml* dosyalarının oluşturma sırasındaki doğruluğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="1a44c-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="1a44c-118">SDK ayrıca uygulama başlangıç süresini de iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="1a44c-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1a44c-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1a44c-119">Recommended action</span></span>

<span data-ttu-id="1a44c-120">Core 2.1 veya daha ASP.NET kullanıcıları [için, Razor SDK'da](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)precompilation için yerel desteği kullanmak üzere güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1a44c-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="1a44c-121">Hatalar veya eksik özellikler Razor SDK'ya geçişi engelliyorsa, [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)adresinde bir sorun açın.</span><span class="sxs-lookup"><span data-stu-id="1a44c-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="1a44c-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="1a44c-122">Category</span></span>

<span data-ttu-id="1a44c-123">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="1a44c-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a44c-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1a44c-124">Affected APIs</span></span>

<span data-ttu-id="1a44c-125">None</span><span class="sxs-lookup"><span data-stu-id="1a44c-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
