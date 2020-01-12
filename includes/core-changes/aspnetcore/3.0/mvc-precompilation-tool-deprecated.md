---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901749"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="9792f-101">MVC: ön derleme aracı kullanım dışı</span><span class="sxs-lookup"><span data-stu-id="9792f-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="9792f-102">ASP.NET Core 1,1 ' de, Razor dosyalarının ( *. cshtml* dosyaları) yayımlama zamanı derlemesi için destek eklemek üzere `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC ön derleme aracı) paketi sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9792f-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="9792f-103">ASP.NET Core 2,1 ' de, [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) , ön derleme aracının özelliklerini genişletmek üzere sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9792f-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="9792f-104">Razor SDK, Razor dosyalarının derleme ve yayımlama zamanı derlemesi için destek eklendi.</span><span class="sxs-lookup"><span data-stu-id="9792f-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="9792f-105">SDK, uygulama başlatma zamanında geliştirirken derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="9792f-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="9792f-106">Razor SDK varsayılan olarak açık olur ve kullanmaya başlamak için herhangi bir hareket gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9792f-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="9792f-107">ASP.NET Core 3,0 ' de, ASP.NET Core 1,1-Era MVC prederlemesini kaldırma aracı kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9792f-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="9792f-108">Önceki paket sürümleri, düzeltme eki sürümünde önemli hata ve güvenlik düzeltmeleri almaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="9792f-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9792f-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9792f-109">Version introduced</span></span>

<span data-ttu-id="9792f-110">3.0</span><span class="sxs-lookup"><span data-stu-id="9792f-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9792f-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9792f-111">Old behavior</span></span>

<span data-ttu-id="9792f-112">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paketi, MVC Razor görünümlerini önceden derlemek için kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="9792f-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9792f-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9792f-113">New behavior</span></span>

<span data-ttu-id="9792f-114">Razor SDK, bu işlevselliği yerel olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="9792f-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="9792f-115">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paketi artık güncelleştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="9792f-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9792f-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9792f-116">Reason for change</span></span>

<span data-ttu-id="9792f-117">Razor SDK daha fazla işlevsellik sağlar ve derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="9792f-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="9792f-118">SDK Ayrıca uygulama başlatma süresini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="9792f-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9792f-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9792f-119">Recommended action</span></span>

<span data-ttu-id="9792f-120">ASP.NET Core 2,1 veya sonraki bir sürümü kullananlar için, [Razor SDK 'sında](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)ön derleme için yerel desteği kullanmak üzere güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="9792f-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="9792f-121">Hatalar veya eksik özellikler Razor SDK 'ya geçişi engelliyorsa, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun açın.</span><span class="sxs-lookup"><span data-stu-id="9792f-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="9792f-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="9792f-122">Category</span></span>

<span data-ttu-id="9792f-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9792f-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9792f-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9792f-124">Affected APIs</span></span>

<span data-ttu-id="9792f-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="9792f-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
